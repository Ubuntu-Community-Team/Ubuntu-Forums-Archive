---
title: "Streaming video : desperate!"
date: 2008-12-03
forum: Multimedia Software
---

### Post by cedrickinnard on 2008-12-03
Hi all
I'm really desperate on this issue, it makes me want to switch back to windows because making it work on Ubuntu is by far way more complicated. But before I do such a thing, I'm asking for help in case somebody can explain to me, a noobie in the Ubuntu world, how to make streaming video work...
The website I'm looking at ([www.radio-canada.ca](www.radio-canada.ca)) contains both video on demand and live video...
I tried both totem packages, and mplayer packages, installed together or separately, and neither both on demand or live can both work with any of the setups...
on [www.radio-canada.ca/nouvelles](www.radio-canada.ca/nouvelles) there is a dark grey box with a list of videos.  Usually it either does not work at all or (currently with mplayer) it takes FOREVER (several minutes) to load.
on [www.radio-canada.ca/rdi](www.radio-canada.ca/rdi) i'm supposed to be able to watch that channel Live but I cannot make it work.
If anybody of you have any idea which setup and packages I should have installed and which I should have uninstalled, please help me. If for anybody of you it works, please let me know what your setup is...
Please note I don't want it to load in an external player.

It seems on the web that i'm not the only one with this problem but I have not found a solution yet... Thanks in advance!!!

---

### Post by cedrickinnard on 2008-12-10
Anybody?

---

### Post by lduplantie on 2008-12-11
I don't know if this will make you feel better, but I have been having the same problem since 6.10. I think it was better with 7.10 and 8.04. On 8.10 it the worse.

I use mplayer, Firefox 3 and Ubuntu 8.10

I cannot see the news clips but I get live programs without problems. 

Funny also that cbc.ca news clip can be viewed (select the RealPlayer version of the clip)

lcn.canoe.ca works sometimes

You should also enable the medibuntu repositories and install the w32codecs package

Also read this HowTo : [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by hern_28 on 2008-12-11
Is it flashplayer you are having a problem with?

---

### Post by lduplantie on 2008-12-16
I won't speak for cedrikinnard but video clips using FlashPlayer 10 play just fine.

I think it has to do with how radio-canada present their news clips. MPlayer is launched within FlashPlayer in a new window (see screen capture)

Thanks for your help

---

### Post by cedrickinnard on 2008-12-17
Lduplantie
Hi, I get the same as the screenshot above, but therein lies the problem, it takes forever to establish that connection on said port (80)...  When I say forever, it is several several minutes..
I still have to try the different packages...I'm on 64-bit, do I install w64codecs?  Maybe the problem lies in the 64-bit version of all those players and packages!?

---

### Post by doobiest on 2008-12-17
I think the flash player you installed might suck. I had similar problems with streaming youtube video.  There's 3 different flash players to choose from in synaptic, I'd play around with that.

---

### Post by wolfen69 on 2008-12-17
> **cedrickinnard said:**
> Lduplantie
Hi, I get the same as the screenshot above, but therein lies the problem, it takes forever to establish that connection on said port (80)...  When I say forever, it is several several minutes..
I still have to try the different packages...I'm on 64-bit, do I install w64codecs?  Maybe the problem lies in the 64-bit version of all those players and packages!?

this is only my opinion mind you, but unless there is a valid reason to use 64bit ubuntu, i think the average person is better served with 32 bit. it seems more things are coded with 32bit in mind. just my 2 cents. anyway, good luck.

---

### Post by cedrickinnard on 2008-12-17
well having 4 gigs of memory is one of those reasons. But anyway, which flash player were working for you?

---

### Post by lduplantie on 2008-12-17
Hum, I don't know about 64 bits. I am running Ubuntu on pretty basic hardware P3 1GHz 512M RAM, nvidia Quadro2 32M. 

With today's update of Firefox (to 3.0.5) news clip now work with radio-canada. They still take some time to load. Note also that I configured the plugin to use x11 for video and alsa for audio (xv or gl did not work for me) I also set minimum cache at about 1200 and 15%. I use the Adobe flash plugin 10.0.12

I hope this helps

---

### Post by lduplantie on 2008-12-21
I just found a troubleshooting guide on the radio-canada web site. It's obviously in French. I assume that if you are enquiring about radio-canada then you can read French.
You can find it on this page:
[http://www.radio-canada.ca/apropos/aide/aide_rep.asp?IDQuestion=118&IDSection=6](http://www.radio-canada.ca/apropos/aide/aide_rep.asp?IDQuestion=118&IDSection=6)

---

