---
title: "Configuring my connection to use DNS, but it keeps reverting"
date: 2013-06-13
forum: Networking &amp; Wireless
---

### Post by alvinmoneypit on 2013-06-13
I'm trying to stabilize my DNS service as it seems to disappear. Apparently, this is a known phenomena, as it has been posted on "[Open DNS]("https://www.opendns.com/")", my dns provider. I recently reset my DNS and appears to be working after rebooting my 12.04.2 install. What I'm wondering about is [this set of instructions]("https://store.opendns.com/setup/operatingsystem/ubuntu") from Open DNS:
8. NOTE:

To avoid having your settings get revoked after reboots, or after periods of inactivity, you may need to make the following changes via the command line:

$ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
NOTE: The dhclient.conf location may vary depending on you linux distribution.

To locate the correct file you can use:
$ sudo find /etc -name dhclient.conf

$ gksudo gedit /etc/dhcp3/dhclient.conf
# add the following line to the document before the 'require subnet-mask' command

supersede domain-name-servers 208.67.222.222,208.67.220.220;

# save and exit
$ sudo ifdown eth0 && sudo ifup eth0

You may be required to change eth0 to your own network device's name if it uses a non-standard name."

I tried working through these, but they didn't seem to be working as is often the case when you find solutions on the internet. I'm not Ubuntu savvy enough to know if these are the correct commands or not - does anyone know what is the correct way to stabilize my DNS so it doesn't keep disappearing? Please be specific as I'm not really up to speed on terminal commands and knowing how they work. I followed the instructions (I think) in post #12, but after simply adding the server addresses in network edit, when I noticed slow connectivity and decided to check, the server addresses were gone.Thanks.

---

### Post by alvinmoneypit on 2013-07-04
I'm running a D-Link DSL-2540B wired router and found that I could save the settings in the router itself, just type the router address into a browser window address, you'll find you need a password, usually "admin" user name and "admin" password will work.  Then navigate through the menus until you find a place to save your settings.  In my case it was:TOOLS>SYSTEM>"save/reboot".  Now it remembers my DNS settings even though it gets rebooted or loses power.

 There may also be a place where you can download the configuration info for you router to a file on your computer, but I didn't try it.

---

