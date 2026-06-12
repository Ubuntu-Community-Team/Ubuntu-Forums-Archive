---
title: "I am not able to run Acestream on Ubuntu-14.04 64 bits, I need your help"
date: 2016-03-08
forum: Multimedia Software
---

### Post by Popescu_Ion on 2016-03-08
Good Morning to all,

I try to use Ace stream on my Ubuntu-14.04 (64 bits, with ffmpeg installed)
I will describe all starting with acestream installation.

1) I installed "**acestream**" accordingly with **[http://forum.torrentstream.org/index.php?topic=2969.0](http://forum.torrentstream.org/index.php?topic=2969.0)**
    No any error !

2) Now, first, I start the engine: "**acestreamengine --client-console"**. # The output, final part is:
2016-03-08 14:49:30,722|MainThread|acestream.coreapp|use fixed i2i_port: 62062
2016-03-08 14:49:30,881|MainThread|acestream.SocketHandler.InterruptSocket|bound on 127.0.0.1:40493
2016-03-08 14:49:30,881|MainThread|acestream.SocketHandler.SocketHandler|bind: socket bound: host=0.0.0.0 port=8621
2016-03-08 14:49:30,881|MainThread|acestream.LM|listen on 8621
2016-03-08 14:49:31,016|MainThread|acestream.VideoServer|start: addr=127.0.0.1 port=6878
2016-03-08 14:49:31,019|MainThread|acestream.SocketHandler.InterruptSocket|bound on 127.0.0.1:59359
2016-03-08 14:49:31,020|MainThread|acestream.SocketHandler.SocketHandler|bind: socket bound: host=127.0.0.1 port=62062
2016-03-08 14:49:31,020|Instance2InstanceThread-24|acestream.APIServer|run: ready to receive remote commands on 62062
**# Seems to be OK ?**

3) I try to play from console some acestream: [B]acestreamplayer acestream://a72f7e9ec9fbf21395b95ee8545a93978b5adc97
[/B]The complete output is:
[0x1f0a8d8] main interface error: no suitable interface module
[0x1e18458] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x1e18458] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x1eefe08] p2p_access p2paccess error: missing required param name
[0x1eefe08] p2p_access p2paccess error: missing required param name
[0x1eefe08] p2p_access p2paccess error: missing required param name[B] # Who cause this ?
[/B]
4) I try to open the same link, from browser interface. The browser ask which application I should use. 
  I Indicate Ace Player application, after that it is shown imediatelly log errors  (from Ace Player application)
  with approximately same message:
 [COLOR=#ff0000]Error:[/COLOR]

 [COLOR=#000000]Engine could not load "acestream://a72f7e9ec9fbf21395b95ee8545a93978b5adc97" : "**missing required param name**"

5) When I try to start Ace Player, in the bottom of interface it is shown:
Prebuffering 0% (connected to 0 streams)  #[B] And don't find any stream !!!
[/B]After a while is shown:
There are no active peers and streams at this moment  # [B]!!!!

6) Whit the same laptop, some internet connection, from Windows Ace Player run perfect!

Dear gentlemen, please, be kind and help me to solve this problem.
Any suggestion is welcomed here in this list ore to my e-mail: [email]newbielinux@yahoo.com[/email]

Thank you very very much in advance, for you support.

[/B]newbielinux


[/COLOR]

---

