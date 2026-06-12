---
title: "Finding a functioning voice changer for Discord on Ubuntu (Kubuntu)?"
date: 2020-03-22
forum: Multimedia Software
---

### Post by galacticsubaru on 2020-03-22
I've been trying to find (or make) a voice changer for a project I have with some friends for a tabletop gameo ver Discord, which includes (for me) role-playing as a robot. Thing is, I can't find any real-time voice modifier/changer/modulator that works on Ubuntu (Or Kubuntu, the flavor I'm currently using), and can also be detected in Discord as a viable Input Device. Reading other forum posts, I've tried the following:


[LIST]
[*][pyvoicechanger]("https://github.com/juancarlospaco/pyvoicechanger"), which only works on pitch, and Discord can't detect.
[*] Jack Rack, which Discord doesn't support at the moment (See [this issue]("https://support.discordapp.com/hc/en-us/community/posts/360035393592-Jack-audio-support-in-Linux-or-at-least-ALSA"))
[*] And finally, according to these two already asked questions ([one]("https://askubuntu.com/questions/1091606/does-anyone-know-a-good-real-time-voice-changer-for-linux-specifically-ubuntu") and [two]("https://askubuntu.com/questions/421947/is-there-a-way-to-modulate-my-voice-on-the-fly"), sox.
[/LIST]

The last one is the only one I haven't confirmed as "not working" since, according to the mentioned [seconds post]("https://askubuntu.com/questions/421947/is-there-a-way-to-modulate-my-voice-on-the-fly"), it requires outputting the audio to a "null sink", [which neither Chrome nor any other Ubuntu recorder/app detects]("https://i.stack.imgur.com/nK1LK.png").



So, what I want to ask is: ***Is there an alternative to voice changer, being manual modulators using chorus, pitch, etc; or simple voice changers using defined settings ("robot", "giant", "helium voice", etc) that can work with different apps in Ubuntu (That is to say, Kubuntu)?*** (Or at least with Discord)

---

