---
title: "Can't connect to Windows 7 through ssh"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by bkadoctaj on 2010-02-24
Hi everyone,

I've recently installed openssh-client in Ubuntu (9.10 Karmic 64-bit) and I have been trying to set up a connection to my Windows 7 desktop.  Currently, both computers are on the same local area network, but I want to ensure this connection will work over the Internet as well.  Regardless, when I use the following command:

ssh -C <remote ip> -l <user>

I get the following output after about a minute or two:

ssh: connect to host <remote ip> port 22: Connection timed out

<remote ip> and <user> are substituted here for their actual values.  I've turned off the firewall in Windows and I believe I have correctly forwarded the ssh service port through my router, and I am at a loss for what could be wrong.  I'm pretty new to Linux so please go easy on me.  :-|  Thanks.

EDIT:  The <remote ip> I'm using is the one for my router since that's the one that appears on various Internet "what is my IP?" sites.

---

### Post by Baneblade on 2010-02-24
Windows does not support SSH.
There are solutions such as Cygin which will allow you to run Linux apps, but it is a pain to configure and in my last experience with it buggy at best. 

That was sometime ago, so perhaps you will have more luck now. Personally i just use RDP to connect to Windows machines now. You could also use something like VNC which can be tunneled over SSH if you do decide to setup Cygwin.

---

### Post by bkadoctaj on 2010-02-24
> **Baneblade said:**
> Windows does not support SSH.
There are solutions such as Cygin which will allow you to run Linux apps, but it is a pain to configure and in my last experience with it buggy at best. 

That was sometime ago, so perhaps you will have more luck now. Personally i just use RDP to connect to Windows machines now. You could also use something like VNC which can be tunneled over SSH if you do decide to setup Cygwin.

Thanks for the quick answer.  :)  I'm attempting to connect with KRDC but having issues.  As of right now, the screen just hangs after I put in the rdp://<remote ip> and give it a user and password...

---

### Post by Baneblade on 2010-02-24
I think that the remote desktop clients use VNC rather than true RDP. That or an older version of RDP. Windows 7 uses the newer RDPv5 and so is not compatible, you will need to use the Terminal Server Client to connect to the Windows 7 systems.

You may also need to adjust your Windows 7 settings to allow other versions of RDP under the advanced settings for remote desktop conenctions.

---

### Post by bkadoctaj on 2010-02-24
> **Baneblade said:**
> I think that the remote desktop clients use VNC rather than true RDP. That or an older version of RDP. Windows 7 uses the newer RDPv5 and so is not compatible, you will need to use the Terminal Server Client to connect to the Windows 7 systems.

You may also need to adjust your Windows 7 settings to allow other versions of RDP under the advanced settings for remote desktop conenctions.
Hmm... even with the VNC protocol I'm getting the hang.  I must be doing something wrong but I can't get anywhere near what it is...

I really appreciate all of your help.  :)  Sorry, I'm just so new to Ubuntu and I've definitely relied on Windows and Mac OS X to take care of the hard work for me in the past.

---

### Post by Baneblade on 2010-02-24
When you say you are using the VNC protocol, did you install a VNC server onto the windows machine to connect to?

I just use the Terminal Server Client to connect to my Windows machine, which allows me to use the native RDP. Just make sure that you have allowed "Connection from any version of Remote Desktop" under your system properties on your Windows machine. Then it will work just fine.

---

### Post by bkadoctaj on 2010-02-24
> **Baneblade said:**
> When you say you are using the VNC protocol, did you install a VNC server onto the windows machine to connect to?

I just use the Terminal Server Client to connect to my Windows machine, which allows me to use the native RDP. Just make sure that you have allowed "Connection from any version of Remote Desktop" under your system properties on your Windows machine. Then it will work just fine.

I did (attempt to at least) install EchoVNC on Windows.  Additionally, I already have TeamViewer installed (not sure what that will do though).  When I use the Terminal Server Client (with either version of RDP) and I click Connect the window disappears and the application appears to close.  Then I get a pop-up window about two minutes later saying:

An error has occurred.

Autoselect keyboard: blah blah blah...
ERROR: <remote ip>:unable to connect

And then saying that it was unable to connect.  It tries to connect again after like thirty seconds and disappears again.

What should I input for "DOMAIN" if the remote computer doesn't have one?

I also cannot find the option you described in Windows 7.

---

### Post by Baneblade on 2010-02-24
On Windows 7, press start, then type: "Allow remote access"  hit enter.

Choose the middle radio button to allow connections from all version of RDP.

Make sure you are using the internal network address if you are trying to connect from inside your LAN.

---

### Post by bkadoctaj on 2010-02-24
> **Baneblade said:**
> On Windows 7, press start, then type: "Allow remote access"  hit enter.

Choose the middle radio button to allow connections from all version of RDP.

Make sure you are using the internal network address if you are trying to connect from inside your LAN.

Okay, I already had the middle radio button selected.

So, you're right, I was able to connect from within my local network by using the internal IP.  But the main reason for wanting this ability is for when I am at school.  How can I ensure that I will be able to connect externally?

Thanks for all your help and patience so far.  I really appreciate it.  :)

---

### Post by Baneblade on 2010-02-24
Assuming you have correctly forwarded the RDP port (default 3389 i think) from your router to your Windows machine it will work correctly when you are outside of your own LAN if you use your external IP address.

Make sure that you have a static IP or use a service like [DynDNS]("http://www.dyndns.com/services/dns/dyndns/") and you're golden ;)

Enjoy

---

### Post by bkadoctaj on 2010-02-24
> **Baneblade said:**
> Assuming you have correctly forwarded the RDP port (default 3389 i think) from your router to your Windows machine it will work correctly when you are outside of your own LAN if you use your external IP address.

Make sure that you have a static IP or use a service like [DynDNS]("http://www.dyndns.com/services/dns/dyndns/") and you're golden ;)

Enjoy
Alright, sounds good.  :)  Thanks again so much!

---

### Post by Baneblade on 2010-02-24
Don't forget to mark this thread as [SOLVED]

---

### Post by bkadoctaj on 2010-02-24
> **Baneblade said:**
> Don't forget to mark this thread as [SOLVED]

Ah right!  :)  Thanks~

---

