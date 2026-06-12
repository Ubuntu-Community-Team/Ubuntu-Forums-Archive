---
title: "PlayTVs failing"
date: 2014-03-25
forum: Mythbuntu
---

### Post by scotta1 on 2014-03-25
[COLOR=#282828][FONT=helvetica]Hi all, recently setup a Myth backend system with 2x PlayTVs. Running a HP Pro 3000, e8400, 2x 1TB HDDs for storage + separate HDD for OS, 6GB DDR memory. Antenna is brand new, professionally installed, normally gets 70 - 80% signal strength, never glitches or tears on any channel. Running Mythbuntu 12.04.3 with mythtv .25 and no updates (seems to be broken). Tuners set to only record one program each. Having a problem where the recordings fail. Turned on verbose logging with -a option, cant find anything helpful. Noticed that after this happens (sometimes it also screws up live tv) that one or two of the tuners seem to have failed, ie femon -a x shows that the tuner is unable to get a channel. Apologies for not saving the output, but it normally outputs something like[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]status SCVYL | signal c1a4 | snr 011e | ber 00000000 | unc 00000000 | FE_HAS_LOCK[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]for each tuner when all is well, but after the problem occurs its like[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]status S        | signal c1a4 | snr 011e | ber <some large value> | unc 00000000 |[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]Not getting channel lock. Comes good again after a backend reboot. I'm thinking possibly a dodgy powersupply, memory or motherboard or perhaps insufficient USB power. Memory configuration ( 2x 2GB + 2x 1GB) not officially supported by HP, but doubt its related - the thing boots. Don't thing its the PlayTVs that are faulty, problem is affecting both of them.[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]Would appreciate any insight, suggestions or advice that can be offered before I go replacing stuff or upgrading mythtv packages.[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]thanks[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]Scott[/FONT][/COLOR]

---

