---
title: "Dapper Flight 7 *still* doesn't have WPA?"
date: 2006-05-20
forum: Networking &amp; Wireless
---

### Post by geocritter on 2006-05-20
Hi guys,

I'm going nuts ](*,)  ...I still can't get my wifi to work in WPA...I've read every how-to I can get my hands on, but no dice.  I thought it was supposed to have been included by now.  I tried to install NetworkManager, but it didn't do any good, and if that's because I didn't configure something right, well, there's not a whole lot of documentation.  Even the man pages don't really describe what files need to be altered, etc.  I read that Dapper was supposed to do all of this automatically, and ask for the psk key, but it doesn't.

I'm sooooo confused.  Am I missing something really obvious?

Any help would be GREAT!

Thanks,
Dan

---

### Post by Fass on 2006-05-20
To know what you haven't done, you have to tell us what you have done. And what card it is. And if you have it running without WPA. If you have installed wpa_supplicant and network-manager-gnome and not just network manager. And removed all references to the card from /etc/network/interfaces and so on, and so on...

---

### Post by geocritter on 2006-05-20
Ok, right now, I totally reinstalled my system and have about 15 minutes of updates remaining.

1.  I assume that wpa_supplicant is already installed (it was when I was working with it last night).

---> need to install it if it isn't, plust NetworkManager_gnome

2.  Card is Intel 2200 (which uses the ipw driver, unless I'm mistaken)

3.  Works just fine under WEP.

4.  Win XP logging in thru WPA-PSK-TKIP just fine (actually, my wife's is fine too).

5.  Have *not* removed any references in the /etc/network/interfaces config file (I played with that last night but it didn't seem to make any differences.

I'll prepare this stuff after my d/l of updates completes in a little bit.  Then I'll post back before I do anything else.  

Thanks for any help in advance,
Dan

---

### Post by Fass on 2006-05-20
You have to remove or comment out all references to the card in /etc/network/interfaces. Network Manager will ignore your card if you don't. My ended up looking like:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp
#pre-up /sbin/wpa_supplicant -Bw -Dndiswrapper -ieth1 -c/etc/wpa_supplicant.conf
#post-down killall -q wpa_supplicant
```
As you can see, only "lo" is left uncommented.

---

### Post by geocritter on 2006-05-20
Ok, I guess I'll have to wait to post back after getting the other files before I do that, since it'll wipe out all of my connectivity thru my landline, as well.

What next?

Thanks,
Dan

---

### Post by Fass on 2006-05-20
You need to have the following in your /etc/default/wpasupplicant file:

```
ENABLED=0
```
I.e, a zero. Not a 1. 

You should also check out [this thread.](http://www.ubuntuforums.org/showthread.php?t=156319&highlight=network+manager)

There shouldn't be all that much left to do. If you get your card running, the Network Manager Gnome Applet should ask you for your wpa key and once you enter it, will ask you for your pass phrase for the gnome key-ring and then it should connect.

---

### Post by geocritter on 2006-05-20
Thanks for the input.  I'm making notes.  If this works, I'll see if there's a good place to make a wiki for it for dapper.

Downloading network-manager-gnome now, and reinstalling wpasupplicant (just for giggles) via synaptic.  

I'll get back to you when I get back online...

Thanks,
Dan

---

### Post by geocritter on 2006-05-20
!!!!!!!!!!!!!!!!!!!!!!!!!
Holy cow, it worked!!!

Now, to find somwhere to make this sucker a wiki...that was GREAT!  THANK YOU!

1.  install wpa_supplicant
2. install Network-manager-gnome
3.  Comment out everything but "lo" entries in /etc/networks/interfaces
4. Create a file called /etc/default/wpasupplicant, add entry "ENABLED=0"
5.  Reboot
6.  Select your network in the NM icon
7.  Follow the prompts for password, type, etc.
8.  Choose password for keyring (you'll be prompted).
9.  Away you go!:-D

---

### Post by geocritter on 2006-05-20
Oh, one other question...does this procedure have to be re-done everytime I install an updated kernel?

---

### Post by Fass on 2006-05-20
No, it doesn't need to be repeated.

Congrats! Hope I was of service. :)

---

### Post by geocritter on 2006-05-20
Buddy, "Hope I was of service" doesn't touch it.  I spent probably 5 hours last night and re-installed the whole doggone OS this morning over this.  And in 15 minutes it's up and running.  

It's people like you who keep people like me from having strokes while working on this stuff...or at least from giving up altogether on it.

From the bottom of my heart, THANKS A MILLION!

Now...if somebody who knows how to program would write up a script that could be executed to do the same procedure, we'd be in business...!

---

### Post by Fass on 2006-05-20
Much obliged.

One annoying thing about Network Manager is that it asks you for your keyring password every time you reboot. It's a known bug that I'm hoping will be fixed in 0.7. I hear it's already fixed in CVS, but don't trust me on that one.

---

### Post by geocritter on 2006-05-20
Well, I guess that could be a pain, but that's ok; minor inconvenience if it's working ok.  But it will be nice if they fix it.

Thanks so much, again.

---

### Post by davebgimp on 2006-05-24
This really helped me out. Thanks.

---

### Post by wizzard9 on 2006-05-26
I have to say a huge big thanks to you guys - I have followed god knows how many sets of instructions trying to get wpa to work and spent about 6 or 7 hours on it.

Then i find this page and five minutes later successfully connected at last.

thank you, thank you, thank you :D :D :D

---

### Post by Buelldozer on 2006-05-30
Fass,

You wouldn't believe the amount of time I've spent trying to get WPA to work. I followed your directions and 10 minutes later I'm connected and rocking.

Words can't express how happy I am right now.

THANK YOU!

---

### Post by nocturn on 2006-05-31
Sigh, now if NM would just handle fixed IP's *and* activate connections at boot time instead of after login.

I have a directory service (LDAP), so my machine is dead without network.

No WPA for me yet :-(

---

### Post by seatek on 2006-05-31
This was VERY helpful. Thank you all so much.

---

### Post by scifan on 2006-06-01
Btw, if you want to use the wpa_supplicant utility, and if you want to use static IP addresses (I'm one of those poor fools who owns a D-Link DI-624 which has issues surrounding providing a DHCP address when utilizing WPA-PSK security...

(also, if you want to specify mapped interfaces you'd want to utilize this)

---

### Post by pinballkid on 2006-06-01
This made it *so* easy to get wpa working. Thanks!

---

### Post by Titan3025 on 2006-06-02
The keyring password dialog is getting annoying after a while though. I really hope that they push a new version soon.

Second really big problem with this approach is that you won't have wireless networking until you log in. No wireless before that point in time. This is not acceptable for a server mode, or console only system. Network manager should have a global WPA configuration. Indepenant of a specific user.

---

### Post by mellon85 on 2006-06-02
[QUOTE=Fass]No, it doesn't need to be repeated.

Congrats! Hope I was of service. :)[/QUOTE]

I'll make a gold statue for you...

---

### Post by davebgimp on 2006-06-02
I notice now with the new 3.5.3 KDE packages for Dapper released a few days ago, there's an error with Knetworkmanager and Kwallet working together. While Kwallet prompts and stores the WPA key, subsequent attempts to connect still ask for a WPA key and I get a message of an error with Kwallet and that one or more apps are misbehaving. I tried deleting the key from the wallet and re-entering it, but the problem persists. No big deal, but I have to supply the WPA ky each and every time I connect.

---

### Post by tdyer on 2006-06-03
Hi

I have followed the steps as far as i can tell...

i have wpa_sup[plicant installed as well as wpagui and network-manager-gnome

i commented out all lines except for lo

(commented out eth0 eth1 eth2 ath0 and wlan0...i only have 1 ethernet port...confused)

i reboot.

im assuming the network manager icon is the one next to the clock. 
when i click on it i get wired network greyed out. if i plug it in it will show me info about my wired connection.

i have a dlink dwl-g630

it works with wep and no encryption...but now that i have commented it out, it works with nothing.

i tried typing sudo NetworkManager into the terminal but that got me nothing.

help

---

### Post by Ratzilla on 2006-06-03
hmm, i dont get any prompts when i enable the connection...
when you install network-manager-gnome, did you remove network-manager? 
when you referred to the network-manager-gnome icon, thats the one that comes with ubuntu by default right?

---

### Post by vgeneral on 2006-06-04
The network-manager-gnome solution worked like a charm.  I spent hours trying to get my wifi up, using wpa for security but I was getting no where.  I ran into this thread and within minutes, my wireless was up and running.

Thanks again for the solution.

---

### Post by Riona on 2006-06-04
followed the post by geocritters

1. install wpa_supplicant
2. install Network-manager-gnome
3. Comment out everything but "lo" entries in /etc/networks/interfaces
4. Create a file called /etc/default/wpasupplicant, add entry "ENABLED=0"
5. Reboot
6. Select your network in the NM icon
7. Follow the prompts for password, type, etc.
8. Choose password for keyring (you'll be prompted).
9. Away you go!  

Well For me this doesn't work. it fails to find the network connection. 
I have a dell laptop with broadcom wireless. In theory this should work I got wep working.  
I haven't uninstalled WPA _Supplicant  . may try to do that. 

Any ideas ?? 
where are the log files located for this?
Thanks.

---

### Post by entangled on 2006-06-09
I kept failing with wpa until I found a note telling me how to generate the wpa_supplicant.conf file. 
Up to now I have not seen any mention of this process in the forums. Perhaps it is what the network manager programs are supposed to do, but don't always work?

I ran the 'wpa_passkey' program, using my access point id (ESSID) and the text password that I had put into the router for WPA Personal security.
This generated text of the wpa_supplicant.conf file, including a long key value. Copy the new wpa-supplicant.conf file to /etc/wpa_supplicant.conf.

Finally I put the following command into /etc/init.d/bootmisc.sh (this is surely not the best idea but it works for me):
```
sudo wpa_supplicant -Bw -Dwext -iath0 -c/etc/wpa_supplicant.conf
```
where you will need to put in your own value for the interface (ath0 for me). I have no idea if this works for anyone else but it did the trick for me.

---

### Post by pssl220 on 2006-06-09
I still have problems with setting up WPA.  In openSuse 10.1 it was very easy to set this up. With Breazy this was a problem. I read in these forums that lots of people had a problem getting WPA to work. I thought, certainly by the Drapper release this would be fixed. What is a higher priority than secure wireless?  Its not like I have some rare wireless card. I have the ipw2200 intel chips. 

I guess I will stick with SUSE which had no problem with WPA right from the start. Even Knoppix had no problem with WPA and that was with an older version. 

Ubuntu works well with WEP, but who wants to use WEP?

I am disappointed because the Ubuntu communtity seems to be very active and working to make this a great distrubution.

---

### Post by 5h4rk on 2006-07-17
What does "Comment out everything but "lo" entries in /etc/networks/interfaces" mean?

Sorry for my english :(

---

### Post by Fass on 2006-07-17
> **5h4rk said:**
> What does "Comment out everything but "lo" entries in /etc/networks/interfaces" mean?

Sorry for my english :(

It means that you have to put a # before all the lines except the ones about lo. A # before lines in configuration files turns the lines into "comments" which the programmes that parse the file ignore.

---

### Post by forth on 2007-08-03
> **geocritter said:**
> !!!!!!!!!!!!!!!!!!!!!!!!!
Holy cow, it worked!!!

Now, to find somwhere to make this sucker a wiki...that was GREAT!  THANK YOU!

1.  install wpa_supplicant
2. install Network-manager-gnome
3.  Comment out everything but "lo" entries in /etc/networks/interfaces
4. Create a file called /etc/default/wpasupplicant, add entry "ENABLED=0"
5.  Reboot
6.  Select your network in the NM icon
7.  Follow the prompts for password, type, etc.
8.  Choose password for keyring (you'll be prompted).
9.  Away you go!:-D

Oh this was magic.....I could kiss you

:lolflag:

:KS:KS:KS:KS:KS (5 stars)

---

### Post by Joe of loath on 2008-02-17
old thread, i know....

well, i'm not exactley proficient at linux, but i do my best...

i'm having some problems network manager and connecting to WPA networks. I followed the guid TO THE LETTER, but when i go to connect to my network, it just shows 3 methods of encryption, all WEP. i'm confused now, as i've tried everything.

i'm using 6.06 LTS, and a belkin card, with either the ralink 2500 or 2560 chipset. they both use the same driver anyway...

so if someone could help me out, that would be brilliant :D

thanks,
Joe

---

