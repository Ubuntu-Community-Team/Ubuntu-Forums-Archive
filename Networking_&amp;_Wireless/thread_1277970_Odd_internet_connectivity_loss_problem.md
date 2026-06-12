---
title: "Odd internet connectivity loss problem"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by matolo on 2009-09-28
I've got this reeeeealy irritating issue plaguing my Ubuntu Jaunty (9.04) install.  It's an internet connectivity thing.  I guess the best thing to do is describe the issue.

The problem is that I /seem/ to lose my internet connection while doing certain things.  Downloads routinely fail after a few minutes (and by fail I mean they seem to just stop...the progress bar no longer progresses).  The same happens on any internet-related action involving a progress bar.  Streaming music will go for a minute or so then stop.  

I was using Last.FM earlier tonite, and while this problem was happening I tested my connectivity by pinging a live internet address.  Oddly enough, my streaming music kept streaming while the ping was going.  Once I stopped it, the stream failed shortly afterwards.

I don't see any issue normally, such as while browsing or whatnot...I would guess that it's because there is no sustained network activity going on and so I don't notice these hiccups.

Anyway, it's driving me nuts, hopefully I've adequately described my problem and someone out there can help.  I'd be happy to supply any additional information needed.

Thanks in advance!

MATOLO

---

### Post by Iowan on 2009-09-29
Almost like something is going into power-saving mode?

---

### Post by matolo on 2009-10-10
> **Iowan said:**
> Almost like something is going into power-saving mode?

Hmmm, no, not really like that.  It's just that when I'm downloading something or streaming something (anything that requires a constant flow of internet traffic), the connection simply stops.  I have to enable a constant ping to something on the internet be able to do streaming or downloading.

Also!  I have Windows7 dual booting on this machine, and I have no such problem when working in that OS.  So it's definitely not hardware-related, it's something with Jaunty.

---

### Post by matolo on 2009-11-10
So, the upgrade to 9.10 didn't help matters.  Am I the only one experiencing such a problem???

---

### Post by Arup on 2009-11-10
There could be several things happening here, either your NIC is going bad or most likely you are facing the dreaded IPV6 issue. In case you are on Karmic, try this. 

Using yout favorite editor using sudo, edit /etc/default/grub and change 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to 
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"

then 
sudo update-grub

After that reboot and surf to see if the issue goes away.

---

### Post by matolo on 2009-11-14
I'm gonna guess it's IPv6, as my Windows partition has no such issues.

HOWEVER...I don't have a /etc/default/grub file.  Is there anywhere else this file may live?

Thanks!

MATOLO



> **Arup said:**
> There could be several things happening here, either your NIC is going bad or most likely you are facing the dreaded IPV6 issue. In case you are on Karmic, try this. 

Using yout favorite editor using sudo, edit /etc/default/grub and change 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to 
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"

then 
sudo update-grub

After that reboot and surf to see if the issue goes away.

---

### Post by Arup on 2009-11-14
> **matolo said:**
> I'm gonna guess it's IPv6, as my Windows partition has no such issues.

HOWEVER...I don't have a /etc/default/grub file.  Is there anywhere else this file may live?

Thanks!

MATOLO

Are you on Karmic or Jaunty?

---

### Post by matolo on 2009-11-14
Karmic...upgraded from Jaunty.

> **Arup said:**
> Are you on Karmic or Jaunty?

---

### Post by Arup on 2009-11-14
> **matolo said:**
> Karmic...upgraded from Jaunty.

Go to edit connections in network manager. If you are on wired or wireless select that connection and edit and then go to IPV6 tab to see if its enabled.

---

### Post by matolo on 2009-11-14
Ahh, I was trying to be too CLI about it :P  

Hrm, it shows IPv6 as "Ignored".  I assume that means disabled since that greys out all the remaining options under that tab.

Aaaand we're back to square one :(  Not configured for IPv6, NIC hardware is fine, and I still have to run a ping to stream audio or download anything.


> **Arup said:**
> Go to edit connections in network manager. If you are on wired or wireless select that connection and edit and then go to IPV6 tab to see if its enabled.

---

### Post by Arup on 2009-11-14
> **matolo said:**
> Ahh, I was trying to be too CLI about it :P  

Hrm, it shows IPv6 as "Ignored".  I assume that means disabled since that greys out all the remaining options under that tab.

Aaaand we're back to square one :(  Not configured for IPv6, NIC hardware is fine, and I still have to run a ping to stream audio or download anything.

That most likely means DNS not working, have you entered the right DNS. Are you on DHCP?

---

