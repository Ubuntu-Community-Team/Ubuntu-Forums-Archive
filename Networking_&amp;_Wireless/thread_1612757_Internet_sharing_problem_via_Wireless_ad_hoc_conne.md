---
title: "Internet sharing problem via Wireless ad hoc connection"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by Aref.Ariyapour on 2010-11-03
Hi every body.

I am trying to establish an adhoc connection in my ubuntu 10.10 and share my cable internet throughout this connection with my Android phone. I have read some guides but I couldn't be successful.(I have another windows mobile, and it couldn't connect too)
I have installed Firestarter in order to enable internet sharing. My main Problem is that, no one can obtain IP adress from the adhoc connection, whether Firestarter is active or not. what should I do in order to make the other devices gain IP address from this connection. If I have to set static IP what should I do exactly?
Please help, to find out how to handle this problem.
Thanks so much

---

### Post by Aref.Ariyapour on 2010-11-04
Any solution?

---

### Post by Hakimjo on 2010-11-04
Hi Aref, I don't have the solution for your problem, sorry.  But I do want to do the same thing as you ;-) and am looking for a HowTo.  Is it right that I should install Firestarter and I should be able to pass my cable pppoe connection on to a second machine via a WiFi card ?  In my case, I am already anticipating an additional problem, as my provider checks the machine's identity.  Will my second machine (the phone) have its own identity or will it be under the name of the first one (the linux with Firestarter) ?

Hope we will manage

j

---

### Post by Aref.Ariyapour on 2010-11-04
> **Hakimjo said:**
> Hi Aref, I don't have the solution for your problem, sorry.  But I do want to do the same thing as you ;-) and am looking for a HowTo.  Is it right that I should install Firestarter and I should be able to pass my cable pppoe connection on to a second machine via a WiFi card ?  In my case, I am already anticipating an additional problem, as my provider checks the machine's identity.  Will my second machine (the phone) have its own identity or will it be under the name of the first one (the linux with Firestarter) ?

Hope we will manage

j

Hi dear Hakimjo.
I have used this HOWTO:
[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)
and based on this guide, I installed the firestarter. It says that fire starter enables Internetsharing between two network interfaces, like eth0 and wlan0. This is all I know about firestarter and I think yeh we should do this (for your first question).
For your second question, I am not pretty sure, but I think there would be no problem for you and you can share your Internet with the other devices in your home network, and I think they can only identify the machines, directly getting service from their server, but keep in mind I said I am not sure.

Please if you found a solution, share with me.
Thanks a lot.

---

### Post by Aref.Ariyapour on 2010-11-10
every body,
Someone please help us

---

### Post by lopcaf on 2010-11-14
Hi! 

I've managed to share the internet connection via wifi to my Android mobile. 

What I did is brutal, but at least shows where the problem is: I purged Firestarter (i.e. Removed completely), then creating a new wireless network form the host is enough for sharing internet. NB Some Android phones cannot recognize an Ad-hoc connection, but you can patch the wpa_supplicant in the Android OS. Google phone-specific instructions.

the command for purging:

**sudo apt-get --purge remove firestarter**

**[COLOR=Red]NOTE[/COLOR]**!! This is not wise to do at all. The firewall administrator is installed for a reason.  

Does anyone have the proper configuration for the firewall via firestarter, such that the phone can get an IP?

Saludos

---

### Post by Aref.Ariyapour on 2010-11-14
> **lopcaf said:**
> Hi! 

I've managed to share the internet connection via wifi to my Android mobile. 

What I did is brutal, but at least shows where the problem is: I purged Firestarter (i.e. Removed completely), then creating a new wireless network form the host is enough for sharing internet. NB Some Android phones cannot recognize an Ad-hoc connection, but you can patch the wpa_supplicant in the Android OS. Google phone-specific instructions.

the command for purging:

**sudo apt-get --purge remove firestarter**

**[COLOR=Red]NOTE[/COLOR]**!! This is not wise to do at all. The firewall administrator is installed for a reason.  

Does anyone have the proper configuration for the firewall via firestarter, such that the phone can get an IP?

Saludos
Hi dear lopcaf.
I have done what you said before installing the Firestarter. But my Android phone cannot obtain IP address from the connection. I have managed to share Internet in windows 7 and my android phone can obtain IP address easily, but I don't know why the android or the other devices can not get IP address from adhoc connection in ubuntu.

---

### Post by lopcaf on 2010-11-15
Hi Aref.Ariyapour,

Which kind of security protocol are you using? I'm using *WEP 40/128-bit key*.

Hope this help.

Best regards

---

### Post by Aref.Ariyapour on 2010-11-16
> **lopcaf said:**
> Hi Aref.Ariyapour,

Which kind of security protocol are you using? I'm using *WEP 40/128-bit key*.

Hope this help.

Best regards

For Understanding whether i can do it or not, I was using no security protocol.

---

### Post by lopcaf on 2010-11-20
Hi, 

does anyone know how to configure properly Firestarter to share internet via a wifi adhoc connection with an Android phone? 

Help will be appreciated. 

Thanks

---

### Post by lopcaf on 2010-11-25
No ideas?

---

### Post by lopcaf on 2010-12-09
Solved: I installed Gufw instead of Firestarter and I can make an Ad-hoc connection with no problem.

Hope it helps.

---

### Post by Hakimjo on 2010-12-09
Cool - I have worked around my problem with an external router BUT I am sure the solution will come in handy in the future or for others.

---

### Post by Aref.Ariyapour on 2010-12-18
> **lopcaf said:**
> Solved: I installed Gufw instead of Firestarter and I can share an Ad-hoc connection with no problem.

Hope it helps.

Hi dear lopcaf,

So happy that you have found the solution. I have installed Gufw, but what should I exactly configure in it, in order to enable internet sharing via my adhoc connection.

---

### Post by amir_pasha on 2010-12-19
This internet connection sharing is really complicated in Ubuntu.
I have been searching for this problem for months but couldn't find a solution, doesn't work at all.
Please someone give a simple solution for god's sake!
Pleaease...

---

### Post by spiky001 on 2010-12-19
hi are you sharing with a pc/laptop or a phone?

---

### Post by lopcaf on 2010-12-20
@[Aref.Ariyapour]("http://ubuntuforums.org/member.php?u=1176765") I didnt have to make any configuration with Gufw. 

To share internet, just create an adhoc connection doing the following:

1) Right click on the NetworkManager Applet
2) Create New Wireless Network...
3) I use the security protocol WEP 40/128-bit

Once created, you should be able to see the network in your android. If you dont, you might need to patch the wpa_supplicant on your phone. Google the model-specific instructions for your phone. 

Hope this is clear enough.

---

### Post by lopcaf on 2010-12-20
[LEFT][@spiky001 ]("http://ubuntuforums.org/member.php?u=915355")

I'm sharing pc/laptop to phone. 
[]("http://ubuntuforums.org/member.php?u=915355")[/LEFT]

---

### Post by peterguirguis on 2011-01-13
Hope im not too late to this thread
if your android phone can't get an ip from shared ad hoc connection simply install dnsmasq```
sudo apt-get install dnsmasq
```
or alternatively configure your android phone manually to give it static ip

---

### Post by nesquik on 2011-01-22
Hi.

I'm not able to set up an ad-hoc connection either, using 10.10.

I want to use my laptop's Internet connection on my iPhone. On Windows 7 I used Connectify to do that.

Tried several tutorials.

Please help!

---

