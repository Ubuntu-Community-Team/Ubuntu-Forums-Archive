---
title: "Going nowhere (Homenetwork)"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by picknick on 2010-01-22
Hi everyone! I don't know what to do, I'm looking for some tutorials but I'm going nowhere...

issue: I've a desktop with Xubuntu 9.04 (wired) and a notebook with Ubuntu 9.10 (wireless), both with Samba installed. The Xubuntu one is a samba-server for a windows network (other pc at home). 
I don't know what to do to see the Ubuntu notebook with the server... I'm think that adding some lines at the smb.conf would solve this problem but I really don't know...

If you suggest any other configuration I would accept it.

I have a router-modem.

Thanks a lot! See ya.

---

### Post by Iowan on 2010-01-22
Can the machines ping each other?

---

### Post by picknick on 2010-01-22
> **Iowan said:**
> Can the machines ping each other?

Affirmative.

picknick

---

### Post by Iowan on 2010-01-22
Do you plan to have Windows boxes on the network?  If not, NFS may be a viable option. Otherwise, these should get you started:
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")

---

### Post by oldefoxx on 2010-01-23
You are not giving consistent details in your descriptioms.  You indicate that the notebook is wireless, and the desktop is wired.  For them both to connect through the modem to the internet, the router would have to support both wireless and provide some ethernet ports, typically 4.  For them even to ping each other, they both have to connect through the router.  Now some notebooks also have ethernet ports, meaning they can be wired to the router as well.  Need more details on what you have and how connected.

I haven't worked with samba, but in networking, your router can be set up as a gateway, meaning each ethernet port is sort of like on a separate LAN and does not relate to the other ports (LANs), or set up as though bridged, meaning everything that connects through that router appears to be on one LAN on the port side, and therefore essentially visible to each other.  But whether they are actually visible to each other can depend on things like what protocol and services are enable on each, what domainn or workgroup each is part of, and so on.

I agree, that there is far too little documentation online as how to set up your own network, and I guess there are several reasons for this:

If you have already learned how, you don't need a document
Knowing how does not mean that you will document it yourself
If you don't know how, then the lack of documentation hurts.
You can do what you are doing, which is post questions on forums.  That should eventually produce some good answers if the thread keeps going.
Lots of Threads just die before that point, so keep asking.
Search with related terms to see if there are answers found elsewhere.
Remember to post back links to the best ones to help others.

One thing you might think would be out there are router guides or manuals, but most instructions apparently are on the install CD.  The router can be talked to via a web brower, usually at address 192.168.1.1 or 192.168.0.1, depending on the brand name.  If running Windows, there may be software tools, some called Wizards, to help you with some of the many settings in the router.  From Linux, you pretty much have to go the manual setup route.

Just trying to give you an idea of what you are involved in.  Going far enough to enable some form of encryption, preferably WPA, WPA2,
or a mixture of both, would be an excellent idea so as to protect your network from prying eyes.

There are several questions I have about router settings that I am having trouble finding answers to:

What does this setting do?  What should it best be set to? What happens if I set it to something else?

In trying to set up everything, what order should I do the settings in?
What should I do after I have made all the changes?  Is there a way I can go back if something is messed up?

In my searches online this evening, I did find one OEM that had several manuals in PDF form available through the internet.  I also looked, and there is a PDF extension for OpenOffice that I got, so that I can get those documents into the Writer. These are not for the router I have, but the sequence of doing setup in the router manually should help me with a different brand and model.  I hope so anyway.  I also feel I could use some help, as this is my first time around in this area.

---

