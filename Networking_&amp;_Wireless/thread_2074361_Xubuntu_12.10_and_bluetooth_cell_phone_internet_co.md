---
title: "Xubuntu 12.10 and bluetooth cell phone internet connection"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by stabbmesiter on 2012-10-21
Hi, 
      Hopefully I can get help to enable connectivity via my bluetooth USB to cell phone (nokia) to internet. 

 Where I live there is no broadband landline (no tarmac on the roads either) but there is cell phone internet access - cheap too!). Hence my quest.
  
 I do try various DE's and have only EVER managed to get my cell phone connected to the internet (and tx/rx) with Mandriva (2009 and 2011) Mageia2 (fork of Mandriva) and Fedora 17. 

 What I am seeing under Xubuntu is really frustrating (same with lubuntu and slackware)....trying things out in VirtualBox before putting onto the the hd for real along with the other Os's. 

 Blueman finds the phone no problems, I can connect to the phone and browse no problems. I can setup a DUN no problems and I can watch the connection on the phone establish itself - looks EXACTLY like it does in Mageia. When connected I'm notified that internet in now available via ppp0 under network manager (I can't find Network Manager, just Internet connections (under which I can setup a mobile broadband link but cannot (ever) initiate it))

ifconfig -a shows ppp0, eth0 and lo connection 

 I try Network access under blueman  and the same but for bnep0. 

 Really like the look of Xubuntu 12.10 (runs FAST under VirtualBox and am drooling to try it out unrestricted) and would love to install as my main OS (do like xfce and would like to use 4.10) (not too powerful PC). But to do so I would have to kick another one out. Hence VirtualBox....I have found if it works there it works in the real world

So, if any techies could help me out I would appreciate it. I have to delete/re-install bt devices so ask for lots in one go please...save me a bit of fiddling around. 
 I'm not technical so please use idiot speech i.e. specific (VERY) instructions and assume I know nothing...not too far from the truth 
  
Could it be an mtu issue (seems to be set to 1500 which is high?)...if so how do you change it?

I've done a lot of looking and there is so much info out there I got myself confused.

Also, how do you get the text (tty output stuff) displayed in those snazzy boxes in the forums...never worked that one out

 All the best and thanks in advance.

---

### Post by stabbmesiter on 2012-10-21
Just read through my original post and realised I did not say what the problem is. All looks Ok but I cannot connect to anything....Firefox, software updates etc. 

Sorry about that...my head was obviously up my fundamental.

---

### Post by Merrattic on 2012-10-21
I am guessing you need to make the network connection on your host PC for things to work through a VM. 

Are you not able to find even just 5GB of space on your HDD to do an install of Xubuntu?

---

### Post by stabbmesiter on 2012-10-21
I could install directly but at the cost of trashing an already installed distro.Which I would do if I could get bluetooth working in a VM environment.  In VirtualBox I have added the PC USB bluetooth chip/dongle and all is recognised. As mentioned it seems to work but I can't connect to anything i.e DUN and/or NAP successful, the phone connects (I watch it do it) and then....nada. No access  I guess I could clonzilla the dev and restore when I see the same problem in the 'real' install.  Just trying to be lazy but guess it's time to backup stuff again. Just hoping there was a clever techie resolution or maybe (even better) someone pointing out that I'm a twonk and telling me what I'm doing wrong.  Regards...

---

