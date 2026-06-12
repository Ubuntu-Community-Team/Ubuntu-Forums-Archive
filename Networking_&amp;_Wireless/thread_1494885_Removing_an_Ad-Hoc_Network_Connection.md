---
title: "Removing an Ad-Hoc Network Connection"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by kirkster86 on 2010-05-27
I cannot seem to stop my computer from broadcasting an ad-hoc connection. I set it up using networkmanager, but now I cannot delete it. I searched Google and ubuntuforums for an answer, but no luck. Any ideas?

---

### Post by purelinuxuser on 2010-05-27
> **kirkster86 said:**
> I cannot seem to stop my computer from broadcasting an ad-hoc connection. I set it up using networkmanager, but now I cannot delete it. I searched Google and ubuntuforums for an answer, but no luck. Any ideas?

What happens when you right-click on the Network Manager applet, click "Edit Connections," select your ad-hoc network and delete it?

---

### Post by kirkster86 on 2010-05-27
> **purelinuxuser said:**
> What happens when you right-click on the Network Manager applet, click "Edit Connections," select your ad-hoc network and delete it?

It deletes it as a saved connection from network manager but the ad-hoc network is still being broadcasted.

---

### Post by purelinuxuser on 2010-05-27
> **kirkster86 said:**
> It deletes it as a saved connection from network manager but the ad-hoc network is still being broadcasted.

How about right-clicking on applet, disable networking, then re-enable?  Or just click on the applet and hit "disconnect" under the ad-hoc network name.

---

### Post by kirkster86 on 2010-05-27
> **purelinuxuser said:**
> How about right-clicking on applet, disable networking, then re-enable?  Or just click on the applet and hit "disconnect" under the ad-hoc network name.

No luck with the first. When I click disconnect, it still shows it as an available network connection to choose from and I can still see it from my other computer.

---

### Post by purelinuxuser on 2010-05-27
> **kirkster86 said:**
> No luck with the first. When I click disconnect, it still shows it as an available network connection to choose from and I can still see it from my other computer.

The network still shows up on other computers because they haven't updated their scans yet.  If you update them the network should be gone.

---

### Post by kirkster86 on 2010-05-27
> **purelinuxuser said:**
> The network still shows up on other computers because they haven't updated their scans yet.  If you update them the network should be gone.

I've tried all of the options you've suggested so far many different times today. It is still being broadcasted. 

Is there any way to bring it down using the terminal or does network manager write the settings to a file somewhere that I can delete?

---

### Post by purelinuxuser on 2010-05-28
> **kirkster86 said:**
> I've tried all of the options you've suggested so far many different times today. It is still being broadcasted. 

Is there any way to bring it down using the terminal or does network manager write the settings to a file somewhere that I can delete?

If you *really really* want to stop that network, try the following commands:
```
sudo service network-manager stop
sudo ifconfig wlan0 down
```

That stops Network Manager and disables the wireless interface!  A little extreme though... :P

---

### Post by jt.waleson on 2010-07-04
> **purelinuxuser said:**
> If you *really really* want to stop that network, try the following commands:
```
sudo service network-manager stop
sudo ifconfig wlan0 down
```

That stops Network Manager and disables the wireless interface!  A little extreme though... :P

Ah this worked for me, I had the same problem, the created network kept popping up, even after restarts.

I disabled the interface with your commands:
```
sudo service network-manager stop
sudo ifconfig wlan0 down
```

then I right-clicked on the network status icon, deleted the ad-hoc network and then restarted the network service:

```

sudo ifconfig wlan0 up
sudo service network-manager start

```

Thanks!

---

### Post by yakshbuntu on 2010-09-18
Goto Applications --> Accessories --> Passwords and Encryption Keys

You should see a Passwords default or login default, whichever is default expand and delete the password you created for your adhoc connection

Log out and log in again, wireless will ask you to key in password, cancel

Now goto Network Manager --> right click and select Edit Connections --> select the adhoc connection which you created and delete it

Now logout and login back, this should permanently delete ad hoc connection created (it worked for me)

---

