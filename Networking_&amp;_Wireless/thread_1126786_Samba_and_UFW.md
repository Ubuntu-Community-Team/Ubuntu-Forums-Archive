---
title: "Samba and UFW"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by The Funkbomb on 2009-04-15
Good day.

I am trying to get my Windows machine and my Ubuntu machine to file share (and eventually printer share).  Baby steps.

About the computers:

1.  Computer 1 is a desktop hardwired to the network.  It runs Win XP Pro.  It has a static IP address of 192.168.1.101.

2.  Computer 2 is a laptop that connects via wireless.  It runs Ubuntu 8.10.  It has a static IP address of 192.168.1.100.

I have UFW enabled on the Ubuntu machine like so:

```
192.168.1.100 139/tcp      ALLOW   192.168.1.101
192.168.1.100 445/tcp      ALLOW   192.168.1.101
```

When I'm on the XP Pro computer, I can see the Ubuntu computer on the network.  I can access it, map the network drive, share files.  That works fine and groovy.

The issue is when I'm on the Ubuntu computer.  I cannot access the Windows workgroup.  The workgroup name is MSHOME.

I understand ports 137 and 138 need to be open using the UDP protocol.  When I open them like this:

```
192.168.1.100 139/tcp      ALLOW   192.168.1.101
192.168.1.100 445/tcp      ALLOW   192.168.1.101
137/udp                    ALLOW   Anywhere
138/udp                    ALLOW   Anywhere
```

It works.  I can see MSHOME but cannot access it.  I think I cannot access it because of permissions issues.  I use a different name on my Windows computer.  That's a different issue though, I think.

I do not want ports 137 and 138 UDP open to the entire network.  Even though I use router security, I still see that as a major breach in security.

When I try to limit ports 137 and 138 UDP to the Windows computer's IP address(192.168.1.101), I can no longer see the Windows workgroup.

Can anyone help me set this up so it works and I'm still secure?

---

### Post by superprash2003 on 2009-04-16
you could try accessing windows shares this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by uncle-c on 2009-04-16
Which version of Ubuntu are you using ? I use 8.10 and I too could not access my workgroup or xp share when going  --->>Places -->>Network and browsing. However, when going --->>Places-->>Connect to server and choosing the service type "windows share," I could browse my xp share. I have my UFW set to deny everything except on  port 22 and 5900  from my internal network.
I had a query posted up in a similar thread and superprash2003 kindly found out that it could be a bug. Can you access the share via command line ?

---

### Post by The Funkbomb on 2009-04-16
That does work!  :D

I don't share too many files so it's no big deal.

Thanks though.

---

### Post by Funkydonut5000 on 2009-04-16
I too have had some strange occurrences with not being able to view my network through the network file browser.  Sometimes it's there, and sometimes it's not.  File sharing with my windows clients still works though.

My bid problem is not being able to share an external usb drive (200 gb) attached to the ubuntu machine.  It's configured the same as the other shared items but no dice.  Hopefully with a little searching I can find a work around.

Funkbomb....great name.  Keep it funky bro.

---

### Post by superprash2003 on 2009-04-17
are you not able to write to the device?? or not accessible at all?

---

### Post by The Funkbomb on 2009-04-17
Actually, this problem is not solved.

When I remote desktop into the Win XPpro machine from my Ubuntu machine, I can see, access and do everything to my managed Ubuntu drive.

When I'm on the desktop itself, I cannot.  Weird.

---

### Post by Andrew_P on 2009-10-29
I think the culprit is ufw.  If I open a terminal window and type ```
sudo ufw disable
``` then type ```
sudo /etc/init.d/samba restart
``` everything works fine after that:  I can see and access Windows shares and Linux shares on my home LAN from one of my Linux boxes, and vice-versa from the various Windows machines.  I'm running Ubuntu 8.10 on two machines; the only one that has problems with accessing the network is the one on which I one day typed "ufw" at a command prompt.  It seems to have permanently messed up some firewall setting, and the only way to get it to behave for the duration of a session is to type the two commands described above.  Unfortunately, I need to go through this routine every time the machine is rebooted; it would be an acceptable workaround if the steps could be put into a script that runs automatically.

My Netgear WGR614 wireless router has an excellent firmware firewall that protects my whole LAN from the outside world, and I'd rather have no firewall in Ubuntu at all, much less a defective one.

---

