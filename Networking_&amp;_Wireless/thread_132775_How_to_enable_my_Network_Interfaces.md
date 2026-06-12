---
title: "How to enable my Network Interfaces"
date: 2006-02-18
forum: Networking &amp; Wireless
---

### Post by vincentaii on 2006-02-18
Hi all,

I've just installed Kubuntu 5.10 onto my Fujitsu Lifebook P5010 and during the install it detected my 2 network interfaces, ethernet and wifi. It then tried to set up the dhcp but as I wasn't connected to the net that failed. I then chose "don't set up dhcp at this time". I think that was my biggest mistake.

Now when I boot into my kubuntu and go into the Network Connection setting, it shows both my eth0 and eth1 disabled, and no matter what I do I can't enable them! 

I can't even get to Admin mode here coz the button for it is missing.... by pressing tab and blindly pressing enter I managed to get to the point it asks for my root password, but when I put it in it just goes back to the same page.... other setting pages are fine and I'm able to get to Admin mode (except for user settings).

I tried to enable the networking interfaces at the "processes" (I think that's what its called) so that it starts up at boot, but that didnt help. What am I missing?

Another problem I'm having is that my modem is not detected at all. I read somewhere that the problem cud be that my laptop has a winmodem... if so, what do I do?

Any help appreciated guys. I tried looking thru the forum but cud find nothing that addresses my problem.

Forgive a noob for his questions.....

Thanks!
Vince

---

### Post by bscbrit on 2006-02-19
Please clarify a few things.  When you say the Admin button is missing, do you mean you cannot find the Administrator button on the GUI configuration display?  ( There is probably a better way of asking that but I'm a Gnome man myself).

Can you enter recovery mode at boot-up?  In which case, you can still configure everything but from the command line and not through a GUI.

Yes, its possibly a winmodem but I would leave that problem until next.  If you get the network up and running will that give you internet access, or do you still need the modem (i.e. are you dial-up access)?

ps You probably haven't got a 'root' password - use your _own_ password, although I don't use Kubuntu so I could be wrong....

---

### Post by vincentaii on 2006-02-19
Hi there,

"When you say the Admin button is missing, do you mean you cannot find the Administrator button on the GUI configuration display?"
Yes, but it seems that it is missing only in the Network Connection display, but exists in the other displays (but doesn't work for the User Account settings"). I'm still able to bring up a dialogue box where it asks me to enter my root password (by blindly tabbing and entering as I previously mentioned), but it doesn't do anything thereafter.

"Can you enter recovery mode at boot-up?  In which case, you can still configure everything but from the command line and not through a GUI."
I believe I can as the recovery mode is stated in my GRUB, but once I'm in I'm pretty much lost.....

"Yes, its possibly a winmodem but I would leave that problem until next.  If you get the network up and running will that give you internet access, or do you still need the modem (i.e. are you dial-up access)?"
I need both ethernet and dial-up to work as I use one at home and the other at office... I've come across a thread which discusses winmodems in more detail and how to (possibly) get it up and running, so I'll give that a go, but for my ethernet I have no idea where to start.

"ps You probably haven't got a 'root' password - use your own password, although I don't use Kubuntu so I could be wrong...."
By default my root password is the same as my own password it seems.... tested and it works for the other config settings, so no problem there. To change it, however, is as I can't get in to my User Account settings....

I find Kubuntu beautiful in every aspect, and it boots up superbly..... my only problem is the above, which if truth be told probably came about from my own doing....

Appreciate any pointers, thks!

Vince

---

### Post by bscbrit on 2006-02-19
I cannot help with fixing the Kubuntu user interface - I don't know enough about it to do that.  But this forum might - it is Kubuntu specific:

[http://www.ubuntuforums.org/forumdisplay.php?f=99](http://www.ubuntuforums.org/forumdisplay.php?f=99)

Do you know your network details i.e. gateway, DNS settings etc?  If so, we can set them from the commandline to get your network up and running.  To help, please go to a commandline and post back the results from the following command:

ifconfig

Finally, I would use the winmodem forum to resolve your modem problems - I would imagine that there will be numerous people there with the expertise to help solve your particular problem.

---

