# Too Many Commands

Too Many Commands is an Among Us mod that provides chat commands and an control panel. Commands can be used by the local player and another player with permissions
## Setup and permissions

Open the menu with **F7**. The **Host** tab lists connected players and lets you grant or remove each command permission. The **Non Host** tab has direct Ban, Jail, RandomTP, Sabotage, and Repair actions, plus permission toggles for `/ban`, `/jail`, `/randomtp`, `/sabotage all`, and `/repair all`. Select a player before changing that player's options. Permission data is saved by friend code in `BepInEx/config/HostCommandRelay.permissions.json`.

The **Affects the person who used the command** option controls whether an all-player action includes its command user. **Can affect you** grants the selected player host-target access. The command display options control the local echo, local confirmation messages, and lobby-wide accepted-command notices.

Other players need the relevant permission enabled before their command is carried out. The local player is unrestricted. Host-only operations, such as spawning maps, still need to run on the host client.

## Command reference

### Color and appearance

- `/color <color>` — Set your own color by its in-game name, such as `/color red`.
- `/color <player name> <color>` — Set another player's color. Use the player's full name when needed; `/colour` is also accepted.
- `/rainbow <player name>` — Start cycling the named player's color. Use the command again to stop that player's cycle.
- `/rainbow all` — Toggle rainbow cycling for everyone.
- `/rainbow stop` — Stop all active rainbow cycles.

### Player actions

- `/ban <player name>` — Remove a player. On the host client this uses Among Us's host kick/ban action. In the Non Host tab, the Ban button and `/ban` permission use ventilationsystem exploit
- `/ban all` — Apply the same removal action to eligible players. The **Affects the person who used the command** option controls whether the command user is included.
- `/kick <player name>` and `/kick all` — Use the host kick action.
- `/jail <player name>` — Repeatedly send the selected player to the map's jail vent. Run it again for that player to release them.
- `/jail all` — Toggle jail for eligible players, subject to the command-user and host-target options.
- `/jail stop` — Release everyone currently being jailed.
- `/randomtp <player name>` — Repeatedly teleport the player to a random vent, approximately every half second. Run it again for that player to stop.
- `/randomtp all` — Toggle random vent teleports for eligible players.
- `/randomtp stop` — Stop all active random vent teleports.
- `/kill <player name>` — Have the host kill the target during a match. When someone other than the host issues it, the host briefly shapeshifts into that player, sends the kill, shapeshifts back into itself, and returns to its saved position. Dead targets are allowed.
- `/kill all` — Kill all eligible connected players, including the issuer or host when target settings allow it. The host frames the issuer once, sends the kills, and restores its appearance and position.
- `/kill loop player <player name>` — Send up to 300 murder attempts. `/kill loop stop` cancels the active loop. Dead targets are allowed.
- `/eject <player name>` or `/eject player <player name>` — During a meeting, make every living player cast a vote for the target. The target must be alive.
- `/make <player name> guardian angel` — Change the target's role to Guardian Angel.
- `/make <player name> impostor ghost` — Change the target's role to Impostor Ghost.
- `/make <player name> crewmate ghost` — Change the target's role to Crewmate Ghost.

### Match and lobby controls

- `/start` — Start the match from the lobby.
- `/end` — End an active match using the normal Crewmate-by-task end reason.
- `/endmeeting` — Close the current meeting.
- `/disable game ending` — Toggle the host-side game-ending suppression. Use it again to toggle it off.
- `/force crewmate victory` — End the current match with a Crewmate victory.
- `/force imposter victory` or `/force impostor victory` — End the current match with an Impostor victory.
- `/imposter amount <0-6>` — Set the requested Impostor count for the next match. `/impostor`, `/imposters`, and `/impostors` are accepted spellings.
- `/assign <player name> <role>` — Assign a valid Among Us role name, such as `Engineer`. In lobby only.
- `/spawn lobby` — Create a LobbyBehaviour object.
- `/despawn lobby` — Despawn one tracked LobbyBehaviour object.
- `/spawn <map name>` — Spawn a map prefab. Supported names are `skeld`, `mira hq`, `polus`, `airship`, and `fungle`.
- `/spawn all` — Spawn those five map prefabs in sequence, with a short pause between each.
- `/despawn map` — Despawn one tracked map object.
- `/despawn all maps` — Despawn all tracked map objects. `/despawn all` is also accepted.

### Sabotage and repair

- `/sabotage all` — Start the sabotage systems supported on the current map. A non-host client sends the system updates through the host. The exact systems depend on the map.
- `/repair all` or `/repair all sabotages` — Repair supported active sabotages. A non-host client routes supported repairs through the host. Fungle Mushroom Mixup repair still requires the host client.

### Game settings

- `/change <setting> to <value>` — Change a lobby setting before the match starts. Use values with units where appropriate, for example `/change speed to 1.5x`, `/change kill distance to short`, or `/change confirm ejects to off`.

Supported numeric settings include speed, kill cooldown, Crewmate and Impostor vision, Shapeshifter cooldown and duration, Guardian Angel cooldown and protection duration, Scientist cooldown and battery charge, Engineer cooldown and vent time, Phantom cooldown and duration, Tracker cooldown/duration/delay, Noisemaker alert duration, Viper dissolve time, Detective suspect limit, Impostor count, max players, emergency meeting count/cooldown, discussion/voting time, taskbar mode, and common/long/short task counts. Kill distance accepts `short`, `medium`, `long`, or `0`, `1`, `2`.

Supported on/off settings are Visual Tasks, Confirm Ejects, Anonymous Votes, Shapeshifter Leave Skin, Impostors Can See Protect, and Noisemaker Impostor Alert. Boolean values accept `on`/`off` or `yes`/`no`. If chat censors the word `speed`, use `/change 5 * to 1.5` or `/change ***** to 1.5`.

### Tasks, reveals, and meeting chat

- `/clear all tasks <player name>` or `/clear all tasks for <player name>` — Remove all assigned tasks from the target.
- `/flood tasks <player name>` or `/flood tasks for <player name>` — Assign the target the full byte range of task IDs.
- `/reveal <player name>` — Send the selected player's role to chat from the host client.
- `/reveal all` — Send every player's role to chat, one reveal at a time.
- `/reveal all imposters` — Reveal only players whose current role is Impostor.
- `/reveal stop` — Cancel pending bulk role reveals.
- `/votespammer` — During a meeting, repeatedly send “Did Vote” notes for players at about one-second intervals. Use `/votespammer stop` or run `/votespammer` again to stop.
- `/help` — Send a command guide. Anticheat mode sends short line-separated messages, limited to 120 characters, 1.5 seconds apart. +25 mode sends the guide in one message with separate lines. A second request is ignored while a guide is in progress; leaving the lobby resets it.
