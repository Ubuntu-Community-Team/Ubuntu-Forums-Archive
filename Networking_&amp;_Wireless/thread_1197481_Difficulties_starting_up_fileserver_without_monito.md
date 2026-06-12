---
title: "Difficulties starting up fileserver without monitor"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by arnoldus on 2009-06-26
I configured a Samba fileserver with Jaunty. Everytime I reboot without a monitor attached to the computer, I can not SSH or VNC to the box. The fileserver and -sharing still works though. 
Is there a configuration that enables me to boot the PC so that it loads the screens even with no monitor?

---

### Post by jimv on 2009-06-26
The simple answer is to just get rid of the GUI altogether (install the server version of Ubuntu) and not worry about it.  The command line is pretty easy after you get used to it.

You can install Webmin to allow some easy remote administration via a webpage of the file shares and other server features.

---

### Post by arnoldus on 2009-06-26
Thanks, I'll hopefully get to that in a while, but ATM I'm not comfortable enough to do that yet, I literally just ran the point & click installer. I'd rather have the GUI working.

Is this a bug or a bad config? I'm not sure, other OS boot up fine with no monitor.

---

### Post by romeroagnelli on 2009-06-26
I suppose this question would be misplaced but i'll still ask it:

Did you download any VNC Server package?
Did you install any firewall that's blocking ports?

I have found that the answer to the above two questions solves the problem. Best of luck.

---

### Post by romeroagnelli on 2009-06-26
All VNC servers have their own Display drivers ao its not a matter of loading the screen.

A very good Remote Access Method is to use the NoMachine NX.

Download and install the debian packages from the website. That should help you get what you want.
[URL="http://www.nomachine.com/"]
http://www.nomachine.com/[/URL]

---

### Post by arnoldus on 2009-06-26
I didn't install anything, just use the normal remote viewing available in Ubuntu. No firewall.

I'll also look into the NX software, but first let's see if it's necessary or not.
(BTW, if the VNC should be the problem, why can't I SSH into it, this should be independent)

---

### Post by ericab on 2009-06-26
i would seriously suggest moving to ubuntu server...
i know you said your not 100% comfortable with the commandline, but with webmin, you basically dont ever need to use it.
take it into consideration.
myself, a few days ago i switched from ubuntu desktop on my fileserver, to ubuntu server, and i honestly couldnt be happier. origionally i was afraid id be kicking myself making such a jump (gui to no gui, especially since i was not comfortable with cmdline) but with webmin, your totally, completley covered.

---

### Post by swerdna on 2009-06-26
> **arnoldus said:**
> I didn't install anything, just use the normal remote viewing available in Ubuntu. No firewall.

The Gnome vnc server is installed by default (package is called "vino"). If you want any other variants you'll have to install it/them. And vino will not activate itself by default. You have to be an active server.

---

