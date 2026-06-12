---
title: "No Internet On 8.10,  Please Help!"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by raiderpig on 2009-11-18
I'm very new to Ubuntu and I installed 8.10 from a CD that I got in a back of a book.  Now that I've installed it, I have no Internet.  I have a Linksys **WUSB54GSC ver. 2 **adapter that I used to connect to a Netgear router using Windows Vista.  I have no way of using an ethernet cable because the router is two stories below me so I need help figuring out how I can get connected wirelessly to Internet.  Please be patient and thorough with me because this is my first time working with Linux.  I appreciate any help.  Thanks!

---

### Post by lvlint67 on 2009-11-18
wireless drivers on linux aren't usually something to be tackled by the feint of heart. I usually refer friends to Linux Mint (bloated ubuntu based distro) which more often than not gets things running... although, that is an extreme step to take to fix such a small problem.

if wireless is absolutely critical then i wish you luck. There has been progress made with using windows drivers in ubuntu. Google it. there are tutorials.

---

### Post by raiderpig on 2009-11-18
Thanks!  Attempting to find a guide online.

---

### Post by xifer on 2009-11-18
Make sure that you have no manual config in /etc/network/interfaces.  All lines relating to eth0/wlan0 etc should be prefixed with a '#' to comment out the line. The lines

auto lo
iface lo inet loopback

Are ok - just leave them and comment everything else.



By default there should be a network icon in the taskbar - click on that and you should see available wireless networks.  Select the correct one, enter the authentication requested and it should work.

---

### Post by raiderpig on 2009-11-18
Argh, none of that makes any sense to me as this is my first attempt with Linux.  I COULD move two floors down and hardwire to the Internet.  Would that work?

---

### Post by xifer on 2009-11-18
> **raiderpig said:**
> Argh, none of that makes any sense to me as this is my first attempt with Linux.  I COULD move two floors down and hardwire to the Internet.  Would that work?

Probably would work - but you should not have to do that if your wireless adapter is working.


Can you run a command sh window (terminal)?  You can find it on the menu.

once open type at the prompt

cat /etc/network/interfaces

That will print the contents of the file onto your display and check it is as I described.  If not open any text editor (there are several), navigate to the file and edit it as described.
You will need root permission - should be prompted for password.

might be easiest to try this in the terminal window:

sudo gedit /etc/network/interfaces

to edit the file

The other part is easy - unless you can't see the network manager icon in the taskbar?

---

### Post by JBAlaska on 2009-11-18
> **raiderpig said:**
> Argh, none of that makes any sense to me as this is my first attempt with Linux.  I COULD move two floors down and hardwire to the Internet.  Would that work?

Yes! it should work on hardwire, but don't give up on Ubuntu yet. You can get it working.

Try this [Link](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29) to install the wireless driver.

Edit: better still, for a new user, this might be easier, I usually use a native linux driver but with some modification you can use the windoze one, this guide also includes drinking beer..bonus. [Guide](http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb54gsc-on-ubuntu-8.04.1-solved-664463/)

---

### Post by raiderpig on 2009-11-18
> The other part is easy - unless you can't see the network manager icon in the taskbar?


Don't see a network manager icon in taskbar.  Just see a speaker icon, date/time, firefox, mail, help, Applications, Places, and System.  

Still going to try what you wrote though.  Wish me luck!


Edit: Can't do the windows driver (beer idea) because apparently I don't have ndiswrapper installed and I need Internet to do that :(

---

### Post by raiderpig on 2009-11-18
> might be easiest to try this in the terminal window:

sudo gedit /etc/network/interfaces

to edit the file

showed up as:
auto lo
iface lo inet loopback

unsure about what to do next...

---

### Post by raiderpig on 2009-11-18
> Try this [Link]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29") to install the wireless driver.

Have to download Ralink driver :(  

Probably going to wait until tomorrow and migrate my desktop downstairs and try to download driver when hardwired, see if it works and then make it back upstairs.

---

### Post by xifer on 2009-11-18
If you're sure you need that driver then ok.  Am not so sure myelf.  

The /etc/network/interfaces is fine.  So leave it alone.

Just need to get the networkmanager running - seems like it maybe has indeed not recognised your card.

Type this in your terminal window and see if anything shows up:

sudo NetworkManager

---

### Post by xifer on 2009-11-18
If you're sure you need that driver then ok.  Am not so sure myelf.  

The /etc/network/interfaces is fine.  So leave it alone.

Just need to get the networkmanager running - seems like it maybe has indeed not recognised your card.

Type this in your terminal window and see if anything shows up:

sudo NetworkManager

---

### Post by Dude-PWB- on 2009-11-19
Go into synaptic package manager and install ndiswrapper and ndsigtk.

Then download your windows driver for your adapter and extract it. Open ndiswrapper from system > administration > Windows wireless drivers and add your windows driver in there, That should get your wireless up and running for you.

---

