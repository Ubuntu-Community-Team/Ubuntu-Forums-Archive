---
title: "channels work in VLC but not in myth 8.x"
date: 2008-11-13
forum: Mythbuntu
---

### Post by dibuntux on 2008-11-13
In mythbuntu 7.10 my HVR1110 card was working correctly and found all channels on Mediaset2 network. 
Now, since all versions of mythbuntu 8 (significantly improved, thanks) the same hardware cannot detect the above network and all associated channels.
The network is correctly found in scan with parameters in dvb-t/rome-it file, but the so produced channels.conf cannot be imported.
The network can also be viewed using VLC, just by inputting the freq (762000000Hz). What I note is that PID numbers are wrong... I can watch the channels Canale5, Italia1 & Rete4 using the PID service23, service24 & service25, reported by scan as encrypted channels. But of course this does not happen with a DTT box: channels are detected correctly.
If I input the freq directly in myth setup it just does not lock to any network.
So I believe something is very wrong with DTT scan and mythtv. 
Everything else works perfectly.

Thanks for helping

My config:
AthlonXP 1700 512MB
Nvidia FX5200
Skystar 2.6
Hauppauge HVR1110
Mythbuntu 8.10

---

