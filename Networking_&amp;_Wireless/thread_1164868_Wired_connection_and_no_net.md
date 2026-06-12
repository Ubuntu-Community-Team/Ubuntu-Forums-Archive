---
title: "Wired connection and no net"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by charkoal on 2009-05-20
I have a problem accessing the internet from my laptop which is connected to the pc through a LAN cable the network icon shows its connected but I cant access the net on it.

---

### Post by superprash2003 on 2009-05-20
go to the ubuntu terminal and type **ifconfig** and post output , we first need to see if your ubuntu machine is able to get an ip address..

---

### Post by Iowan on 2009-05-20
If machine has valid IP address (avahi's 169.254.X.X indicates a problem), next check */etc/resolv.conf* for DNS information.

---

### Post by doas777 on 2009-05-20
and then the output of 
```
route
```

---

### Post by charkoal on 2009-07-30
> If machine has valid IP address (avahi's 169.254.X.X indicates a problem), next check /etc/resolv.conf for DNS information.

I typed in the code to check for DNS but it says permission denied.

---

### Post by Newfoundlander on 2009-07-30
> **charkoal said:**
> I typed in the code to check for DNS but it says permission denied.

Try
```
cat /etc/resolv.conf
```

If you need to be root for permissions then try
```
sudo cat /etc/resolv.conf
```

---

### Post by charkoal on 2009-07-30
ok that worked thanks, what do I do now ?

---

### Post by Newfoundlander on 2009-07-30
> **charkoal said:**
> ok that worked thanks, what do I do now ?

The resolv.conf is basically corrupted so you'll need to replace it with one that is able to let you connect to the Internet.

You'll need to boot into a Live CD and copy the /etc/resolv.conf file (either copy it onto a USB stick or write down the contents on paper) then boot back into your non-connecting setup and replace it.

---

### Post by charkoal on 2009-07-30
> You'll need to boot into a Live CD and copy the /etc/resolv.conf file (either copy it onto a USB stick or write down the contents on paper) then boot back into your non-connecting setup and replace it. 

Sorry i dunt know how to do that :(

---

### Post by Newfoundlander on 2009-07-30
> **charkoal said:**
> Sorry i dunt know how to do that :(

Put your Ubuntu install disc into your drive and restart.  It will boot to a menu screen.  Select the first option "Try Ubuntu without any change to your computer" -- this is the Live CD portion.

It will take a bit longer than usual because it's running off the CD instead of the hard drive.  When the desktop appears, go to Places > Computer > File System > etc.  Copy the resolv.conf file to a USB stick if you have one or right-click and open with text editor and write down the lines.

Take out the CD and restart to enter your normal setup.  Copy the file from your USB stick to your desktop and enter the following into your terminal...

```

cd Desktop
sudo cp resolv.conf /etc/resolv.conf

```

If you didn't use a USB and only wrote it down, then...

```

sudo gedit /etc/resolv.conf

```

Then delete the contents and replace with the stuff your wrote down.  Save the file and reboot.

---

### Post by AdnrwV2 on 2009-08-01
Hello.
I think I have the same problem and I did what you suggested with copying the resolv.conf file.
But it didn't work.
Any ideas on what I can do now?

---

