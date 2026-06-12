---
title: "Remote Windows via Ubuntu"
date: 2006-02-10
forum: Networking &amp; Wireless
---

### Post by sascha on 2006-02-10
I am having no problems remotely accessing and controlling my Ubuntu (Breezy) machine via Windows XP using Ultra VNC, however I would like to be able to remotely access and control my Windows XP machine via Ubuntu. I can't find any threads offering guidance in this endeavour, is this even possible to do and if so how?

Thank-you

---

### Post by cwaldbieser on 2006-02-10
[QUOTE=sascha]I am having no problems remotely accessing and controlling my Ubuntu (Breezy) machine via Windows XP using Ultra VNC, however I would like to be able to remotely access and control my Windows XP machine via Ubuntu. I can't find any threads offering guidance in this endeavour, is this even possible to do and if so how?

Thank-you[/QUOTE]
The rdesktop program is probably what you want to use.  It uses RDP (remote desktop protocol) which is what various flavors of Windows use.

---

### Post by skirkpatrick on 2006-02-10
Except XP Home.  Get and install RealVNC on your Windows box and use Terminal Server Client on Ubuntu to access it.

---

### Post by dcstar on 2006-02-14
[QUOTE=cwaldbieser]The rdesktop program is probably what you want to use.  It uses RDP (remote desktop protocol) which is what various flavors of Windows use.[/QUOTE]
The tsclient package front-ends rdesktop, try that.

---

### Post by funkjunkie on 2006-02-18
im using the power pc flavor of 5.10 trying to get remote desktop access to an XP pro machine.
i can ping the remote server using the terminal, and use "remote desktop access"  using osx thru the same sonicwall tz170 VPN router.

when i add the info in the client and click connect, the GUI just disappears.  
and nothing happens.

the "tsclient package"already seems to be installed and active

my gut feeling is that is a power pc tweak that needs to happen, but i couldnt prove that. i just installed ubuntu for the first time this week, and im a born again linux believer and a struggling newbie, but any help would be great.
many thanks.

---

### Post by cwaldbieser on 2006-02-18
[QUOTE=funkjunkie]im using the power pc flavor of 5.10 trying to get remote desktop access to an XP pro machine.
i can ping the remote server using the terminal, and use "remote desktop access"  using osx thru the same sonicwall tz170 VPN router.

when i add the info in the client and click connect, the GUI just disappears.  
and nothing happens.

the "tsclient package"already seems to be installed and active

my gut feeling is that is a power pc tweak that needs to happen, but i couldnt prove that. i just installed ubuntu for the first time this week, and im a born again linux believer and a struggling newbie, but any help would be great.
many thanks.[/QUOTE]
Well, sometimes if you use the command line version (rdesktop), it will spit some error info into the terminal that will help.

---

### Post by funkjunkie on 2006-02-18
yikes.  a hint as to how to do that..  the cmd? :-k
 gksudo /usr/sbin/rdesktop
?

---

### Post by Schmic on 2006-02-19
[QUOTE=sascha]I am having no problems remotely accessing and controlling my Ubuntu (Breezy) machine via Windows XP using Ultra VNC, however I would like to be able to remotely access and control my Windows XP machine via Ubuntu. I can't find any threads offering guidance in this endeavour, is this even possible to do and if so how?

Thank-you[/QUOTE]

I set up a remote vnc last night from ubuntu to windows last night. originally i tried just using windows remote desktop but found it more annoying than it needed to be. I had already been using Tightvnc from my headless ubuntu to my desktop ubuntu and that works incredibly well.

So i just downloaded the win32 version and installed it on my xp. It doesn't work quite as well as with ubuntu (screen refresh on the vnc is a little laggy) but that can be tweeked easily when i get too annoyed with it:) 

If you want to try it [http://www.tightvnc.com/]("http://www.tightvnc.com/") and on ubuntu you can install it through apt-get or synaptic once you have the universal repositories, or you can just use the vncviewer in the ubuntu main repository which works fine as a viewer.

I found the win server gui very simple to use and fairly adaptable. Hope this helps you

---

### Post by funkjunkie on 2006-02-19
hm. thanks for the suggestion.
not sure ill get clearance to install something like that on my machine at the office.  a friend running an old p3 installed ubuntu but his Terminal Server Client works without a hitch. anyone else out there running the power pc flavor experience this?

---

### Post by cwaldbieser on 2006-02-19
[QUOTE=funkjunkie]yikes.  a hint as to how to do that..  the cmd? :-k
 gksudo /usr/sbin/rdesktop
?[/QUOTE]
```

$ rdesktop <hostname-or-ip-address>

```
Or for fullscreen (alt-enter to get back to Ubuntu):
```

$ rdesktop -f <hostname-or-ip-address>

```
And if you want to mount a directory as a shared drive (with Win2k3 or XP only):
```

$ rdesktop -r disk:temp=/home/myuser/temp <hostname-or-ip-address>

```
NOTE: sudo is NOT required.

---

### Post by funkjunkie on 2006-02-19
\\:D/  thank you.  that worked!!

---

