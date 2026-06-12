---
title: "Wired network drop out, when uploading?"
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by Chad Howitzer on 2012-02-20
Hi,
Firstly I would just like to say that I am new to Ubuntu so apologies in advance :)

I have just built a basic Desktop for web browsing ect and wanted to try my hand at Ubuntu.

The installation was good and I really like the interface. However, When everything was up and running I noticed that the network activity kept dropping to zero.

I am using the latest version of Firefox and as far as I can tell, still getting used to where everything is, all of the drivers are up to date to.

I have a pretty standard set up, wired connection to an ADSL router, and the system picked up the Ethernet cable straight away. I ran all of the updates and driver updates and opened Firefox which appeared to be working fine.

I started to go through the usual websites making sure flash etc was working and had the network activity window open to keep an eye on the speeds. When I opened up Facebook and tried to click on some of the pictures the activity dropped to zero. I had to refresh the page again to get any activity back but was unable to view any of them.

After trying various sites and options I went onto the speed test website and ran the test. The download section ran very fast but as soon as the upload section started all network activity dropped to zero again.

I am using an Asrock K10n78fullhd-hsli R3.0 motherboard

I am not sure what information would be usefull to post to help but I'd be very grateful for any advice.

Thanks very much

---

### Post by gordintoronto on 2012-02-20
What version of Ubuntu did you install?

---

### Post by roelforg on 2012-02-20
Your lack of info won't help any of us help you.
Try the following commands in a root console (terminal->"sudo bash" (w/o quotes)).
```

ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
ping 8.8.8.8
lshw -C network
uname -a

```

If you wanna be really helpful, run "lshw" in the root console.

Post the output of the commands and maybe we'll be able to help.

(note: this is rather odd, i've seen/solved network issues from the weirdest kind, heck i even fixed some probs with coax networks, i've still got a coax/aix/10-base-t hub in my closet for emergency's (never needed it, my 10/100/1000mb/s switch is rocksolid, but still))

---

### Post by Chad Howitzer on 2012-02-20
> **gordintoronto said:**
> What version of Ubuntu did you install?

It was Ubuntu 11.10

---

### Post by praseodym on 2012-02-20
Please show the terminal (CTRL+ALT+T) outputs of the commands "roelforg" showed.

---

### Post by Chad Howitzer on 2012-02-23
> **roelforg said:**
> Your lack of info won't help any of us help you.
Try the following commands in a root console (terminal->"sudo bash" (w/o quotes)).
```

ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
ping 8.8.8.8
lshw -C network
uname -a

```
 
If you wanna be really helpful, run "lshw" in the root console.
 
Post the output of the commands and maybe we'll be able to help.
 
(note: this is rather odd, i've seen/solved network issues from the weirdest kind, heck i even fixed some probs with coax networks, i've still got a coax/aix/10-base-t hub in my closet for emergency's (never needed it, my 10/100/1000mb/s switch is rocksolid, but still))
 
 
Hi, 
Thanks for the help so far, sorry for the delay in posting back.
 
Here is the following output from,
 
*Removed Posting*
 
Please let me know if i can add any more info. As i say, i'm new to Ubuntu and any help is much appriciated
 
Thanks again

---

### Post by Chad Howitzer on 2012-02-28
Any help?

---

### Post by Chad Howitzer on 2012-03-01
Managed to solve this and get everything up and running. Thanks for the initial interest and the terminal codes

---

