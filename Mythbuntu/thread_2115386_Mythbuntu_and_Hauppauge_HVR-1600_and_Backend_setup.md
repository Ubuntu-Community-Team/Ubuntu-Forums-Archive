---
title: "Mythbuntu and Hauppauge HVR-1600 and Backend setup"
date: 2013-02-12
forum: Mythbuntu
---

### Post by homeeey on 2013-02-12
I'm a total noob so please be kind.  :)

Fresh install of Mybuntu and in backend setup the 1600 is detected, but I can not get the frontend to see the backend.  It doesn't seem like it is continuing run.  The last commands below I check status, it's not running, I start it and then check status, still not running.  Any help is appreciated, let me know what I need to post.  Wearing myself out, and family misses me.

Thanks

```
hometv@hometv-KJ378AAR-ABA-a6430f:~$ dmesg | grep cx18
[   15.671636] cx18:  Start initialization, version 1.5.1
[   15.671845] cx18-0: Initializing card 0
[   15.671852] cx18-0: Autodetected Hauppauge card
[   15.672131] cx18 0000:01:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   15.672141] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   15.677339] cx18-0: cx23418 revision 01010000 (B)
[   15.896485] cx18-0: Autodetected Hauppauge HVR-1600
[   15.896487] cx18-0: Simultaneous Digital and Analog TV capture supported
[   16.020041] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   16.035693] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
[   16.035699] DVB: registering new adapter (cx18)
[   16.092915] cx18-0: DVB Frontend registered
[   16.092918] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
[   16.092971] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
[   16.093006] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   16.093040] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
[   16.093043] cx18-0: Initialized card: Hauppauge HVR-1600
[   16.093131] cx18:  End initialization
[   16.098296] cx18-alsa: module loading...
[   16.223525] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   16.346945] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   16.353577] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   17.350761] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   17.369891] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
hometv@hometv-KJ378AAR-ABA-a6430f:~$ 
hometv@hometv-KJ378AAR-ABA-a6430f:~$ sudo service mythtv-backend status
[sudo] password for hometv: 
mythtv-backend stop/waiting
hometv@hometv-KJ378AAR-ABA-a6430f:~$ sudo service mythtv-backend start
mythtv-backend start/running, process 2718
hometv@hometv-KJ378AAR-ABA-a6430f:~$ sudo service mythtv-backend status
mythtv-backend stop/waiting
hometv@hometv-KJ378AAR-ABA-a6430f:~$ 

```

---

### Post by klc5555 on 2013-02-14
Did you complete the entire backend setup? The backend won't run if you leave the setup incomplete by, say, exiting the setup after adding the tuner cards but before setting up the Video Source and Input Connections sections. With the 1600 card, if you intend to use both the digital and analog sections, you'll need to set up a separate Video Source for each, just as though they were completely separate cards.

If you intend to use the analog side of the 1600, did you set the analog side up (in the Add Cards section of the backend setup) as an MPEG tuner (correct!) or as the default V4l Analog card, which won't work and may stop the backend from initializing? The digital side should present no particular problems on post 2009 kernels.

These are the issues that most frequently bite the completely new mythtv user with this particular card. Ch. 3 and following of the mythtv installation manual at [http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index) makes for good reading in regard to setting up a backend so that it runs.

---

### Post by homeeey on 2013-02-14
Thanks for the response. I got it going. Wife and kid only allows me small windows of time to work on it. 
 
All the local stations are digital, being the noob I am, I was thinking that this would be the MPEG. As soon as I figured out that I needed to use the DVB setup (not sure why it detects as samsung) things started working.
 
Then, it was time to get the remote to work, it does.
Then, configure the buttons, they work.
 
Any idea how to get the latest Nvidia drivers working? 310.32. Everytime I try to install them terrible things happen, probably would not be terrible if I knew what I was doing, but last time I tried it would immediately boot to terminal mode.
 
Last night I did this
 
ctrl-alt-f1 to exit UI and enter terminal mode and login
 
```
service lightdm stop
```
 
then 
 
```
sudo  sh ./NVIDIA-Linux-x86_64-310.32.run
```
 
It comes up with a preinstall error. I read in a bug report that people had ignored that without problem, I ignored it also. Installation finished, then I
 
```
sudo reboot
```
 
it rebooted, but in terminal mode, no GUI. I thought I caught a glimse of no displays detected. It was getting late and I recovered by using the apt-get install command to retrieve the latest drivers and install. They installed, but when it booted up GUI I was prompted with a login, that would accept my password, but immediately the password window would disappear, then reappear and want me to login again. I could login as guest. Solved this with 
 
```
sudo chown yourusername:yourusername .Xauthority
```
 
I think tonight I'll try 
 
```

[FONT=Courier New]service lightdm stop[/FONT] 
[FONT=Courier New]sudo init 3[/FONT]
sudo sh ./NVIDIA-Linux-x86_64-310.32.run
[FONT=Courier New]sudo service start lightdm[/FONT] 
```
 
Whadda ya think? Will it make any difference? What is the command to launch gui from command line?
 
thanks

---

### Post by klc5555 on 2013-02-14
It detects as Samsung because that's the manufacturer of the dvb tuner on most 1600s.

Installing Nvidia drivers from the Nvidia download blob is generally more trouble than it's worth in Ubuntu. You could either install the Nvidia drivers provided with your version of Mythbuntu (whatever it is), or if that proves unsatisfactory (there apparently were issues with 2.95.40), 12.04 updates has an "nvidia-experimental" package which includes 3.10.14. You probably won't gain anything significant trying to force 3.10.32 onto your installation in place of the other available options.

---

