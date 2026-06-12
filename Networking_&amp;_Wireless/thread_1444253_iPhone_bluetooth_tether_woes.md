---
title: "iPhone bluetooth tether woes"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by Mr-Roboto-wants-to-party on 2010-04-01
Hi,

I have a 9.10 installed on my USB stick drive and I am trying to get my iPhone to tether with bluetooth.

I followed a guide, (installed blueman, connected to phone, enabled tethering, set to trust device and provide network access).  Very simple really.

The computer connects to the network and says it is successful, and the iPhone has the blue flashing banner saying it is now tethering, but firefox doesn't connect to the internet.

Is there a way to force it to use the new tethered connection???

---

### Post by Mr-Roboto-wants-to-party on 2010-04-05
no one?

---

### Post by Shutter4U on 2010-04-05
I searched for the original thread that I read this solution on, but I couldn't find it. There is one in these forums though.

Anyway, it works for me. You might find it useful too.

The first thing you need to do is create a script to start a bluetooth tethering session. In gedit or whatever your favourite text editor is, create a file with the following in it and save it to your home folder:

```
#!/bin/bash
sudo pand --connect <your bt address> -n
sleep 1
sudo ifup bnep0

```

replace <your bt address> in the example above with the address of your iPhone's bluetooth chip. You find this in your iPhone by going into Settings->General->About and look for Bluetooth followed by a number that looks something like 00:21:fg:i9:3d:43 though the numbers will be different for every iPhone.

You'll need to make it executable and make sure you have the correct permissions to use it. In this example, the file was saved with the filename "panup" and "username" is name you log in with.

```
sudo chmod 700 panup
sudo chown username:username panup 

```

You *should* then be able to connect on the command line by typing
```
./panup

```
in your home folder.

Now, for the script to disconnect.

Again in a text editor create a file with the following in it and save it in your home folder.

```
#!/bin/bash
sudo ifdown bnep0
sudo pand -K
```

save the file and make it executable like the other.
To disconnect just type:
```
./pandown
```
assuming the file was saved as "pandown".

I've been using these scripts for about a week and twice I have had an error come up that said "...connection refused". I have been able to get it working again by Resetting the network settings on the iphone and rebooting it, then going into Settings->General->Bluetooth and tapping on my computers name to get it to connect, then running the "panup" script. After that, it connects and disconnects by just running the scripts.

You can also setup menu items or launchers to run the scripts in gui mode by setting them up to use the command "gksudo ./panup" or "gksudo ./pandown"

:guitar:

---

### Post by AlanR8 on 2010-04-05
Are you sure this is not an Apple issue? My mate with an iPhone and MacBook Pro has to pay Steve Jobs £17 pm for the pleasure of tethering!

---

