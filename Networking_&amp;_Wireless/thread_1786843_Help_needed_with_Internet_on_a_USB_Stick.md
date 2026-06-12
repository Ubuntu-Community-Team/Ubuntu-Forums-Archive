---
title: "Help needed with Internet on a USB Stick"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by harpik on 2011-06-20
Hi all,

I am in Germany right now, and for the internet, I have given a USB Stick: mobilcom-debitel Surf-Stick, XS Stick W14. The problem is, the files on this stick all have .exe extension. I tried to use Wine to make them work, but Wine says that they are not marked as executable. So I tried to change that, but I got a message saying that the files are "read-only", and I cannot make that change.

Can anybody help me with this? I am very new to Ubuntu, so please be detailed as possible.

Thanks!

PS. I am using Ubuntu 10.04 LTS.

---

### Post by Plumtreed on 2011-06-20
You won't need the exe files, right click on the NetworkManager icon, go to edit connections, mobile broadband, click on the add button and follow the steps......

---

### Post by harpik on 2011-06-20
Ok, I think I managed to add it to the list in "Mobile Broadband", but how do I connect it? It doesn't show up in the network list (I am sorry if this is a really stupid question).

---

### Post by harpik on 2011-06-20
Now I have a feeling that I am making a mistake with setup of this. I have a case for this USB Stick, and inside I have the following information: PIN, PUK, Freiaschaltungsnummer (?), and in addition "Login:FONIC" and PIN (same as above). I was told to enter these Login and PIN when the program starts, but as I mentioned before, I wasn't able to run it.

Now, when I add the Mobile Broadband, I chose Fonic as the provider (as there is no choice as mobilcom debitel), and followed the steps. I am not sure what to enter for Number, Username, Password and Network in the Editing dialog. :confused:

---

### Post by sanderj on 2011-06-20
> **harpik said:**
> Now I have a feeling that I am making a mistake with setup of this. I have a case for this USB Stick, and inside I have the following information: PIN, PUK, Freiaschaltungsnummer (?), and in addition "Login:FONIC" and PIN (same as above). I was told to enter these Login and PIN when the program starts, but as I mentioned before, I wasn't able to run it.

Now, when I add the Mobile Broadband, I chose Fonic as the provider (as there is no choice as mobilcom debitel), and followed the steps. I am not sure what to enter for Number, Username, Password and Network in the Editing dialog. :confused:

The wizard fills out everything after selectiing Fonic, doesn't it?

So what happens when you leave everything on default? So don't change anything, and just try the GSM/UMTS connection.

---

### Post by harpik on 2011-06-20
> **sanderj said:**
> The wizard fills out everything after selectiing Fonic, doesn't it?

So what happens when you leave everything on default? So don't change anything, and just try the GSM/UMTS connection.


It fills out some parts: Number: *99#, Username: fonic, password: fonic and APN: pinternet.interkomm.de. It still doesn't appear on the list (I even chose connect automatically, and that doesn't work either). So I entered the PIN that I was given, and that didn't help either.

---

### Post by Plumtreed on 2011-06-20
It should fill everything in automatically so don't add the PIN.

Open Synaptics Package Manager and search for....ModemManager...if not installed, install it and reboot.

---

### Post by harpik on 2011-06-21
> **Plumtreed said:**
> It should fill everything in automatically so don't add the PIN.

Open Synaptics Package Manager and search for....ModemManager...if not installed, install it and reboot.


It just checked it, and it is installed.

Any other suggestions?

---

### Post by Plumtreed on 2011-06-21
Recap were we are, does the connection appear when you left click on the NetworkManager applet?

If 'stick' has an indicator light does it do anything.

Mobile Broadband can be very sensitive in some locations and, on occasion, I have found it necessary to perch by a window in some hotels to get reception.

---

### Post by harpik on 2011-06-21
> **Plumtreed said:**
> Recap were we are, does the connection appear when you left click on the NetworkManager applet?

If 'stick' has an indicator light does it do anything.

Mobile Broadband can be very sensitive in some locations and, on occasion, I have found it necessary to perch by a window in some hotels to get reception.

If I left-click the applet, it doesn't show this connection.

The stick has an indicator light, when I first plug in, it shows 5-6 different colors after another, and then it stops at red. It blinks on and off red light. 

On my desktop, I see an icon for "XSManager". If I click this one, I can see the exe files.

I am sitting next to a window, but I will try different spots to see whether the sensitivity is the issue.

---

### Post by Plumtreed on 2011-06-21
USB-modeswitch and usb-modeswitch data, check to see if these are instaled.

Reboot and see how it goes.

You may have a delay while the broadband connects. In the UK, I have a mobile-broadband stick that needs to be removed and installed again in order to connect.

---

### Post by harpik on 2011-06-21
> **Plumtreed said:**
> USB-modeswitch and usb-modeswitch data, check to see if these are instaled.

Reboot and see how it goes.

You may have a delay while the broadband connects. In the UK, I have a mobile-broadband stick that needs to be removed and installed again in order to connect.


I can see that USB-modeswitch and usb-modeswitch data are not installed. So today I will try to find some internet so that I can install them. I will let you know how it goes. Thanks :)

---

### Post by harpik on 2011-06-21
I installed the usb modeswitch and usb modeswitch data and rebooted, but nothing happened. The light is still blinking red. Moreover, the icon of XSManager does not appear anymore.

By the way, I found on a website that a program called Sakis3g might work, so I installed that too. By following the steps, I entered the PIN number and chose Fonic as the provider. The program seems to be running, and now the color of the stick is green -constantly. However, the connection still does not show in the applet, and my internet still doesn't work.

---

### Post by Plumtreed on 2011-06-21
When I was last in Germany I had a similar 'stick' which I thought was provided by O2? and it worked 'out-of-the-box' in what was essentially Ubuntu 10.10. If you haven't updated recently I would do that.

From memory, I have used 3-4 different sticks in different countries since, when the light is green your signal is weak, blue is good and flashing blue means you are connected. 

My guess is that you do have a connection via Windows that is OK, so you are fairly sure you are in an area in which you are likely to connect.

The 'APN' seems very critical so I would suggest you check the documentation to be sure the correct 'APN' is being inserted and also click the box that allows other users.

---

