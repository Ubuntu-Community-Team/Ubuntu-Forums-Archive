---
title: "Toshiba L640 Wireless BCM4313 Not Working"
date: 2011-11-10
forum: Networking &amp; Wireless
---

### Post by jskandhari on 2011-11-10
I also have a HP Laptop which has BCM4311 and getting Wifi to work on it was easy simply had to **disable** Broadcom STA Driver **install** firmware-b43 and Reboot

I have a Toshiba L640D having BCM4313 Wireless card.

First thing I tried was the above Troubleshooting. Also read the 
BCM4313 solved thread stating to "blacklist bcma" but it didn't work. Only progress achieved so far is that it detects the Wifi Connection asks for Security Key but is never able to connect.

---

### Post by jskandhari on 2011-11-11
SOLUTION
Did some hit and trial and finally got my BCM4313 to work.
None of the Previous threads directly related to BCM4313 helped so here I am mentioning my steps.

Firstly went over to Synaptic Package Manager
>Remove all the Installed Packages related to BCM & BCM 43 // Do check STA in Additional Drivers is deactivated if not please do so before Removing Packages

>Then check whether **bcma** is blacklisted ( in file /etc/modprobe.d/blacklist.conf ) if not then type in terminal
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

>Similarly check whether **brcm80211** is blacklisted ( in file /etc/modprobe.d/blacklist.conf ) if not then type in terminal
```
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

>Reboot

>Goto Synaptic Package Manager
In search simply type **bcm43** ( to easily find all the Packages required to install )
Select the Following Packages for installation ( latest version )
1)bcmwl-kernel-source
2)broadcom-sta-common
3)broadcom-sta-source
4)firmware-b43-installer

It will prompt for additional packages required simply accept them too.

>Reboot

This time round No Wifi is being displayed in the Network Section and if you check
```
rfkill list
```
It also won't be displaying the wifi card will display bluetooth only ( if any )

>Goto Additional Drivers
Activate Broadcom STA

By now your Wireless would be active and ready to connect but still on the safer side

>Reboot

Now if you check Synaptic firmware-b43-installer won't be marked as installed // Mentioning just in case you face with any problems can apply your own Hit and trails.

---

### Post by ken.sailor on 2012-03-27
Sweet!

I've got an hp-2000 with a bcm4314 and this worked perfectly for me (as some other suggestions did not).

Just one question.  Why do you have to install the broadcom-sta-source?

Ken

---

### Post by andreabizz on 2012-04-27
Thank you very much!!!!!1:lol::lol::lol:
It's work in my DELL Vostro 3700 Laptop
This guide works also for ubuntu 12.04 TLS

---

### Post by lossman29 on 2012-04-28
To the OP, I have a BCM 4313 and did all the steps as you mentioned. When I check rfkill after reinstalling packages, it still shows me wireless lan and under that soft blocked and hard blocked.

```

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

OP mentions, we should only see the bluetooth list. That is not the case with me. Perhaps, that's why it still ain't working. Any suggestions?

---

### Post by AdrianP on 2012-05-03
Many thanks *jskandhari*, this (post #2) has worked for me. (Acer Aspire 5741 laptop containing Broadcom BCM43225 wireless)

My problem started after upgrading from 11.10 to 12.04, after which all  references to wireless networks had disappeared from the drop-down  'Network Menu'. Although 'Broadcom STA proprietary wireless driver' was  listed under 'System Settings...' > 'Additional Drivers', it was not  activated, and pressing the 'Activate' button produced the error "Sorry  the installation of this driver failed. Please have a look at the log  file for details: /var/log/jockey.log"

I didn't have to follow your instructions to the end before my wireless  started working again as the Broadcom STA activated automatically at the  second re-boot (directly following the package re-install).

Thank you!

---

### Post by o xavi on 2012-05-03
Hello there,

Thanks for the solution it worked fine in a HP Pavilion dm4 with a BCM4313.

I had tried several ways to fix it before and they just dind't work. This is the simpler and straight forward solution I have found and it works!!

Cheers.
Javier.

---

### Post by biodojo on 2012-06-13
On the Acer Aspire One with the BCM4313 there was wireless but it was unstable on 11.04. I upgraded to 12.04 and it works better, but I am still concerned about occasional drops in connectivity (can't ping) even though Network Manager reports connection. When I go to connection information it is using the brcmsmac driver. Usually waiting a minute restores functioning wifi. Is that the driver you all are using on your machines with BCM4313? Have you noticed connection drops?

---

### Post by ralphd11 on 2012-09-29
It was a pain in the *** but it worked for me.  I had to do it several times.  Thank you

---

### Post by mridul64 on 2013-06-09
Hi lossman,

I am facing a similar problem as yours. I assume that you have fixed it as it has been quite some time since this message has been posted. Can you help me out in solving it please.


Hi OP,

Can you also guide me what to do, my rfkill list gives the exact 6 lines which lossman has just mentioned.

---

### Post by astump97 on 2013-06-17
Just FYI: this worked for me with Ubuntu 12.04 LTS on a Dell Latitude E4200 with Broadcom Corporation BCM4312 wireless card.

---

