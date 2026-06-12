---
title: "Netgear WG511v2 Wireless Works On Dell Inspiron 1100"
date: 2006-04-21
forum: Networking &amp; Wireless
---

### Post by shanep on 2006-04-21
For the FIRST time I am posting something online using my Dell Inspiron 1100 laptop running Ubuntu!  Ive tried this soooo many times (on other Linux distros) always having to go back to Redmond, but YES!  It works!  I take back all the bad things I ever said about Linux and am absolutely ecstatic about Ubuntu!  Its great!

I thought that I should post something useful here as well in case someone did a forum search.

Download the lastest distro of ndiswrapper

Extract it in the tmp folder

Goto System->Synaptic Package Manager

Search for ndiswrapper

Select and install it.
(You might need to be connected to the internet through your ethernet eth0.  Not sure about this.  I was.)

Copy the files from the Drivers->Windows 2000 directory on your Netgear install CD into the tmp folder on your drive (Not sure if you need just the .inf but I copied all four files in the dir.)

Do a google search for how to login as root in Ubuntu.  You will need it before the next steps.

Goto Applications->Accsessories->Terminal

Type: su  (This logs you in as root or Superuser)

Use the password you made for root.

Type:  ndiswrapper -i /tmp/WG511v2.inf (remember files are case sensitive in Linux)

Should say something like: Installed wg511v2...

Type:  ndiswrapper -l

You should see something  like:
wg511v2 driver present, hardware present.

You will only see hardware present if the card is plugged in.

Make the network autoload by typing the following:  sudo ndiswrapper -m

Now we need to add a few lines to the network config file. 

I will present this in the exact way I did it.  If there is an easier way someone will say so Im sure.

Logout of your computer.

Login as:
username: root
password: (The password you made for the root)

Now goto Applications->Accessories->File Browser

Browse to: file system->etc->network

Double click "interfaces"

At the end of the section that says:  #this will be activated automatically by the hotplug subsystem
Add the line:  map wlan0

At the end of the section: #the primary network interface
Add this line:  iface wlan0 inet dhcp 
And this line:  wireless_keymode open

At the very end of the file add:  auto wlan0

Save the file.

The last thing I did was click the two monitors on the toolbar and typed wlan0 in the Name box.  It brought up the signal strength thing and allowed me to click configure and then click wireless network (which wasnt there before) and setup my encryption info.  It picked up the SSID and did everything I would expect it to.

Anyway,  really excited to start using Linux more.

---

