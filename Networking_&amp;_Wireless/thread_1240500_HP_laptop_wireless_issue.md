---
title: "HP laptop wireless issue"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by davidmorgen on 2009-08-14
I just installed Ubuntu 9.04.  Running on a HP pavillion ze4900 laptop.  wireless controller is a Broadcom BCM4306.  Wireless networking is checked, but Wireless networks is greyed out.  I have also read what is written on [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom) but don't really understand what the solution is.  If you can provide help, would be much appreciated!

David

---

### Post by Metaljaz on 2009-08-14
Trying opening the Synaptic Package Manager and do a search for fwcutter. It should say b43-fwcutter. Mark for install and then apply.

If its not there try this from the terminal window:
(Make sure you are using a wired internet connection)

sudo apt-get update
sudo apt-get install b43-fwcutter

Then Go under System > Administration > Hardware Drivers and make sure the driver is activated. If it is activated in the top right hand corner look for the icon for wireless internet connection. Click on the connection to use it. 
Make sure you unplug your wired connection.

---

### Post by davidmorgen on 2009-08-15
> **Metaljaz said:**
> Trying opening the Synaptic Package Manager and do a search for fwcutter. It should say b43-fwcutter. Mark for install and then apply.

If its not there try this from the terminal window:
(Make sure you are using a wired internet connection)

sudo apt-get update
sudo apt-get install b43-fwcutter

Then Go under System > Administration > Hardware Drivers and make sure the driver is activated. If it is activated in the top right hand corner look for the icon for wireless internet connection. Click on the connection to use it. 
Make sure you unplug your wired connection.


[Metaljaz]("http://ubuntuforums.org/member.php?u=196778") - I don't know how to thank you.  I spent literally the whole day trying to get this to work, and it finally works!  I was about to go out and buy a new computer!  YOU ARE A HERO, YOU ARE THE MAN!!!!!!!!!!!!

THANKS!!!!!!!!!!

---

### Post by archanadevi on 2009-08-15
Thank you Mr.Metal. Its great solution.

---

### Post by AKviking on 2009-09-18
Thanks for posting that Metaljaz.  I too have a HP ze4900 and installed Ubuntu 3 times just to go back to Windows because I could not get the wireless networking going.  

Upon finding this thread, I knew it was time to try a 4th time.  Bang!!  It works flawlessly.  In fact it's better than Windows.  With Windows, if I turn on the wireless card, it stays on until I manually turn it off.  With Ubuntu, if there's no open program in need of network, it turns off the wireless card automatically.  Then when I start Firefox or Pidgin, it will turn the card back on.  This is a good thing seeing as how having the wireless card on, it sucks power out of the battery faster.

Thanks.

---

### Post by ExpatEgghead on 2010-03-19
Thank you  Metaljaz. I had upgraded to 9.1 from my previous Ubuntu and the wireless had no problems. I had to reinstall from scratch yesterday and when the wireless stopped completely I got very puzzled.

---

