---
title: "Network Manager dependent upon GUI"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by Levander on 2009-09-26
Why is the little icon is the status bar entirely dependent upon the graphical desktop being loaded?  What if I don't have it loaded and need to get to the network via the command line? Which, as an old time UNIX hand, I do often. 

Often I ssh in and have to restart gdm.  Waiting for the graphical desktop to load before I can get back in is another annoyance.

Having system functionality like networking dependent up graphics entirely goes against the UNIX way.  I'm hoping the developers don't think this is an okay way to do things, because it is a completely departure from the way things have always been done in UNIX.  And, there's no good reason for this change.  It's completely a step back.

That little icon in the system tray, that's called Network Manager, right?

---

### Post by Iowan on 2009-09-26
Um... yes, that's Network Manager - an applet. Applets work best in a graphical environment. Servers (at least the Ubuntu variety) usually come without a graphical environment (desktop...GUI). If you prefer, you can set up your network as the older systems (like my Gutsy) and servers do - via */etc/network/interfaces* file. Unfortunately, interfaces configured that way are ignored by Network Manager... so you can't have it both ways... but you can choose which way.

---

### Post by Levander on 2009-09-27
> **Iowan said:**
> Um... yes, that's Network Manager - an applet. Applets work best in a graphical environment. 

Now that they've got all the code written, it shouldn't be hard to write command line tools to access the same code Network Manager uses to enable/disable the network connections.  Well, unless they've written the thing really poorly and coupled all the GUI and network code together tightly.

> Unfortunately, interfaces configured that way are ignored by Network Manager... so you can't have it both ways... but you can choose which way.

No, thanks.  Now that Ubuntu has changed the default way network connections are handled.  I'd also have to mess with the /etc/init.d scripts to make sure the scripts enable and disable the connections properly.  And, that's just the 1st thing that comes to mind...

Losing any graphical way to switch between wireless networks, another major pain.  Try admining a laptop you have to work on occasionally that he has to remember command line tools to connect to a new wireless network.  Yeah, right.

Ubuntu's made decisions I consider bad before, but this is the first one that's just WRONG.  There's no good reason to have your network connections dependent upon your graphical environment.

---

### Post by bb002 on 2009-09-27
To me it seems if the "Available to all users" IS checked the connection works without having to be logged into your desktop.

Right click the Network Manager Applet -> Edit Connections.
Pick the tab you want then click the connection you want.
Click edit. Enter your sudo password if prompted. In the bottom left is a check box for "Available to all users" make sure it is checked and in the top left "Connect Automatically" is checked too.
Click apply, Enter your sudo password if prompted. Then click close.

Now the the connection should work even without logging into your desktop. Mine does atleast. Hope yours does too. :)

I don't know if this would work for wireless connections, though. :/ I have all mine set to manual connect only.

[edit]
you might want to look into cnetworkmanager. it gives you a CLI interface to NetworkManager. I haven't messed with it myself.
[http://vidner.net/martin/software/cnetworkmanager/](http://vidner.net/martin/software/cnetworkmanager/)

---

### Post by Levander on 2009-09-28
Yeah, great bb002.  I figured there was some way to work around it, but that stuff you posted, makes it look like it's even easier to work around this issue than I was hoping.

It is strange they made it the default that the desktop had to be loaded to access the network.  I've never seen lower level stuff like that be dependent up an end-user desktop in UNIX, ever.

---

### Post by doas777 on 2009-09-28
ok, the reason for this is wifi and laptops.

in the traditional stack, the network is brought up before almost anything else, to enable services to load and bind to it, but you can't do that with a wifi network or a PC that changes network connections regularly. 

the answer is to allow the user to select the wifi network they wanna connect to, but in order to do that you need to have the interface up. this is called a "Userspace technology".

network-manager is for desktops not servers, so whenever i;m setting up a server, (any box that has services on it that other hosts need) I configure the IP properties in my interfaces file as discussed above.

---

### Post by Levander on 2009-09-30
> **doas777 said:**
> ok, the reason for this is wifi and laptops.

in the traditional stack, the network is brought up before almost anything else, to enable services to load and bind to it, but you can't do that with a wifi network or a PC that changes network connections regularly. 

the answer is to allow the user to select the wifi network they wanna connect to, but in order to do that you need to have the interface up. this is called a "Userspace technology".

The vast majority of people who use Wifi cards connect to the same network every time.  Even the people I know who use laptops.  There are travelers who change networks frequently.  It would be easy to provide them with an option not to auto-connect to a network on boot.

In fact, that's how Network Manager already works.  On my box, it automatically connects to the same wireless network every time.  I didn't even configure it to do that.  It just does it.  It doesn't work how you describe it.

The only problem is, the connection goes down if I have to shutdown the GUI for something.  Which, for a system admin adminning other people's laptops and desktops, is often.


> network-manager is for desktops not servers, so whenever i;m setting up a server, (any box that has services on it that other hosts need) I configure the IP properties in my interfaces file as discussed above.

It's clumsy to have to do it two different ways for two different scenarios.  And, it's in no way necessary in this case.

---

