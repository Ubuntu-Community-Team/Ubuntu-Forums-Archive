---
title: "MPD + PulseAudio annoyance with network sinks"
date: 2013-03-29
forum: Multimedia Software
---

### Post by zeero_k on 2013-03-29
I have MPD running on Ubuntu Server 10.04.4 LTS. It sends output to two local audio devices (using module-combine to sync them) and also to two other network sinks, which are windows boxes running the PulseAudio 1.1 Windows binary. So I have three outputs set up in MPD, the local combined sink and the two remote sinks. This setup works pretty well, I use QMPDclient to control playback on the server from any machine, and can send the output to other rooms in the house through the network to the windows boxes. 

But there is one major problem/annoyance: When I have one of the network outputs enabled in MPD, but that computer is turned off or the Pulseaudio client is shut down for whatever reason, then the other sinks/outputs, including the local ones on the server, freak out and cause skipping in the playback. Verbose logging shows buffer underruns, rewinds & such. If I disable the output in MPD to the non-existent sink, then order returns.

This is a significant annoyance. I'm trying to educate my girlfriend on using my MPD setup, but this issue is becoming a stumbling block; it's not obvious that one needs to disable another output to get the others to behave. 

I have also tried using http streaming to the windows boxes, but that suffers from two issues: 1) The stream shuts down when the playlist ends and has to be manually restarted; 2) Really high latency.

Any suggestions? Are there any options to that can be enabled in the MPD or PulseAudio config files? Or some way to manually disable outputs when they disappear on the network?

Thanks!

P.S. Another annoying issue I had was that I was getting a rude pop/click noise once every few minutes when running Pulseaudio 1.1 on one of the Windows Boxes through a SB Audigy sound card, even when no audio was being sent to PulseAudio. This problem went away when I switched to the on-board audio interface rather than the Audigy, which doesn't sound as good, but it's a work-around that I can live with. I'll take any suggestions on this issue if anyone has any ideas.

---

