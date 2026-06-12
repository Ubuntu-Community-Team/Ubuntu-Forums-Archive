---
title: "Atheros AR5008/Gigabyte GN-WI06N-RH driver install problems, Dell Mini, Kubuntu 8.1"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by NoobBiscUiT on 2008-12-22
I recently Purchased the Gigabyte GN-WI06N-RH and was hoping to get it (drivers) installed and working on my dell mini. Hoping that someone here might be able to help me out

I am Have attempted to get this working in both Ubuntu 8.1 and Kubuntu 8.1

I attempted to install the madwifi-ng drivers by using this page:
[http://www.aircrack-ng.org/doku.php?id=madwifi-ng#support_for_atheros_802.11b_g_n_cards]("http://www.aircrack-ng.org/doku.php?id=madwifi-ng#support_for_atheros_802.11b_g_n_cards")

the first divider after all the code says that the AR5008 should be compliant, and that it is in "experimental mode" but still usable.

When i was following the steps on that page, i got errors saying "iwe_stream_add_event" then i followed what the page said and attempted to install the other way, which also didn't work.

i also blacklisted the ath5k.ko and the ath9k.ko in  my /etc/modprobe.d/blacklist directory using nano.

I checked in my BIOS to see if the wireless was enabled also. 

i removed both the madwifi directory in my folder, and the tar.gz i downloaded, then nothing worked after a reboot.

so..i found another page [http://probing.wikidot.com/ubuntu-intrepid-8-10-replacing-ath9k-by-madwifi]("http://probing.wikidot.com/ubuntu-intrepid-8-10-replacing-ath9k-by-madwifi") and i followed the instructions, and as of right now i get nothing.

my ifconfig tells me i have pan0, l0 (local), and eth0. nothing about ath0.

I can't seem to get it to work and i am rather confused, with my last laptop the madwifi install worked great.

any and all help no matter how small is greatly appreciated.
I can give command output if need be also :D 
thanks everyone,


**EDIT:**

I have tried at least 7 different methods of getting the wireless card working on this laptop and i have had no luck.

whenever i finish compiling and all the steps required, and i reboot no wireless device was found.

I dont know if it's a motherboard issue or what...but i cannot get the wireless working in **either ubuntu 8.1 or kubuntu 8.1**


**Guides I Have Followed**
[http://bbechdol.wordpress.com/2008/09/18/installing-madwifi-drivers-for-atheros-ar5418-80211abgn-on-ubuntu-hardy-heron-804/]("http://bbechdol.wordpress.com/2008/09/18/installing-madwifi-drivers-for-atheros-ar5418-80211abgn-on-ubuntu-hardy-heron-804/")


**Edit 2**
I contacted dell over the phone and it seems that it's just a weird incompatibility w/ the laptop.
Neither dell or Gigabyte know what to do, or i guess care to help that much :/ 

Moral of the story though this card will not work w/ the dell inspiron 910 mini, 

hopefully this thread and information saves someone alot of time.

if anyone has any ideas please let me know.

---

### Post by NoobBiscUiT on 2008-12-25
please?

does anyone have any idea?

---

### Post by 2hot6ft2 on 2008-12-25
Ath9k supports that chipset (AR5418 chipset) which is what the AR5008 has as shown here [http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k) so first step would be to un-blacklist ath9k.

---

### Post by 2hot6ft2 on 2008-12-25
I would also try kernel 2.6.27-7 as mine is in that list and mine works with that kernel and ath9k. Mine is the AR5009 and has the AR928X chipset. But it drops the connection if I use kernel 2.6.27-9.

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

Replace intrepid with hardy if you're on hardy

---

### Post by 2hot6ft2 on 2008-12-25
Besides if you're running Intrepid 8.10 you should have gone to this page.
[http://www.aircrack-ng.org/doku.php?id=mac80211](http://www.aircrack-ng.org/doku.php?id=mac80211)
not this one that you link to in your first post.
[http://www.aircrack-ng.org/doku.php?id=madwifi-ng#support_for_atheros_802.11b_g_n_cards](http://www.aircrack-ng.org/doku.php?id=madwifi-ng#support_for_atheros_802.11b_g_n_cards)

Since the new kernels support mac80211 as referenced in the first paragraph on the page you linked to.
> This page only deals with the net80211 version of the madwifi-ng driver. For the mac80211 ath5k version see the mac80211 page. To understand the differences, see mac80211 versus ieee80211 stacks write-up. 

---

### Post by NoobBiscUiT on 2008-12-29
that answers some questions, but also makes more.

> **2hot6ft2 said:**
> Besides if you're running Intrepid 8.10 you should have gone to this page.
[http://www.aircrack-ng.org/doku.php?id=mac80211](http://www.aircrack-ng.org/doku.php?id=mac80211)
not this one that you link to in your first post.
[http://www.aircrack-ng.org/doku.php?id=madwifi-ng#support_for_atheros_802.11b_g_n_cards](http://www.aircrack-ng.org/doku.php?id=madwifi-ng#support_for_atheros_802.11b_g_n_cards)

Since the new kernels support mac80211 as referenced in the first paragraph on the page you linked to.
ok, ya i linked to that page because that is one of the sets of instructions that i followed.

additionally you said:
> **2hot6ft2 said:**
> Replace intrepid with hardy if you're on hardy
so should i replace my kubuntu intrepid distro w/ hardy then?
i did your "sudo apt-get install linux-backports-modules-intrepid-generic" command and nothing came up, 
likely because im on intrepid? 

afterword, i shouldn't blacklist anything then. 

 i should have ath5k, ath9k, mac80211 non-blacklisted.

---

### Post by NoobBiscUiT on 2008-12-29
also what should i do if i cannot find the wireless card at all?
like with lspci, or will it show up after i compile these drivers.

additionally what method should i use to build (install) the drivers since i don't have to blacklist anything.

---

### Post by NoobBiscUiT on 2008-12-30
i just tried everything on this page [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros) and got no results, following the whole thing through :(

---

### Post by kevdog on 2008-12-30
Try this post if you need a working ath9k driver.  For now just forget about madwifi.  Go with ath9k.
[http://ubuntuforums.org/showpost.php?p=5535562&postcount=3](http://ubuntuforums.org/showpost.php?p=5535562&postcount=3)

---

### Post by NoobBiscUiT on 2008-12-31
is the ath9k that i am going to compile from that link different from the one included in a fully updated version of kubuntu 8.1?

also, when i compile drivers from somewhere i should get a wireless device to show up in ifconfig?

i dont have one now.. even though the card is plugged into the laptop correctly w/ antennas and everything :?

:( 
so confused..

i have ath9k on my laptop right now, and ath5k because it is included in kubuntu 8.1.
maybe something will change after i finish these 220 updates?

---

### Post by NoobBiscUiT on 2008-12-31
> **kevdog said:**
> Try this post if you need a working ath9k driver.  For now just forget about madwifi.  Go with ath9k.
[http://ubuntuforums.org/showpost.php?p=5535562&postcount=3](http://ubuntuforums.org/showpost.php?p=5535562&postcount=3)
according to that page, the ath9k was included in the stable release of 8.1 and the alpha releases before it.

if i have the ath9k on my machine what do i have to do to now?

also, when i go to  system > admin > hardware drivers: i get a message that says "no proprietary drivers are in use on this system."

i see the same exact thing on regular ubuntu 8.1 . 

no wireless interface upon bootup, or any extentions.

---

### Post by 2hot6ft2 on 2008-12-31
Ok, 8.10 comes with ath9k. I blacklisted ath5k so there wouldn't be a conflict between the 2 trying to control the card. I boot using the 2.6.27-7 kernel. And it works good.

If I boot with the 2.6.27-9 kernel the wifi keeps dropping. Keep in mind that I don't have the same card as you but mine is in the same list of cards supported by ath9k so I would think that yours would work as well.

I'll go back thru the thread and see where you're at.

---

### Post by NoobBiscUiT on 2008-12-31
ok cool  thanks :D

these ubuntu updates are taking forever.. 

i will blacklist ath5k in the meantime.

if i use the ath9k however, will it be reverse compatible?
i will still be able to connect to b/g wireless networks right?

assuming this works..

---

### Post by 2hot6ft2 on 2008-12-31
> **2hot6ft2 said:**
> I would also try kernel 2.6.27-7 as mine is in that list and mine works with that kernel and ath9k. Mine is the AR5009 and has the AR928X chipset. But it drops the connection if I use kernel 2.6.27-9.

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

Replace intrepid with hardy if you're on hardy
And you replied with
> **NoobBiscUiT said:**
> 
so should i replace my kubuntu intrepid distro w/ hardy then?
i did your "sudo apt-get install linux-backports-modules-intrepid-generic" command and nothing came up, 
likely because im on intrepid? 

afterword, i shouldn't blacklist anything then. 

 i should have ath5k, ath9k, mac80211 non-blacklisted.
No. You have intrepid so you would use the command as it is without changing anything. Changing the command to hardy would be uded IF you were on Hardy which you're not. Nothing to do with changing distros.
> **NoobBiscUiT said:**
> also what should i do if i cannot find the wireless card at all?
like with [COLOR="Blue"]lspci[/COLOR], or will it show up after i compile these drivers.

additionally what method should i use to build (install) the drivers since i don't have to blacklist anything.
[COLOR="Blue"]That would be used IF it's a pci card[/COLOR] There should be NO building of anything it should already be in the system.

As I said in my last post I did blacklist ath5k in the /etc/modprobe.d/madwifi file. That is the only thing I blacklisted.
> **NoobBiscUiT said:**
> is the ath9k that i am going to compile from that link different from the one included in a fully updated version of kubuntu 8.1?

also, when i compile drivers from somewhere i should get a wireless device to show up in ifconfig?

i dont have one now.. even though the card is plugged into the laptop correctly w/ antennas and everything :?

:( 
so confused..

i have ath9k on my laptop right now, and ath5k because it is included in kubuntu 8.1.
maybe something will change after i finish these 220 updates?
You shouldn't have to compile anything. And you say the card is plugged in, and that it's a laptop. Does that mean it's a usb?

If it's usb then you wouldn't use lspci but would use lsusb to show the usb devices.

Hmmm, now where are we....

---

### Post by 2hot6ft2 on 2008-12-31
> **NoobBiscUiT said:**
> 
if i use the ath9k however, will it be reverse compatible?
i will still be able to connect to b/g wireless networks right?

assuming this works..
First there was madwifi which became ath5k which is becoming ath9k if I've followed it right. Yes it would be backwards compatible.

By the way you said you blacklisted ath5k.ko and ath9k.ko as I understand the way things work if it ends with .ko it is either the kernel or has something to do with the kernel so I wouldn't blacklist anything with that extension unless someone would care to correct me on that.

---

### Post by 2hot6ft2 on 2008-12-31
Another thing. Now I see you're using Kubuntu. In that case I think it would be. ```
sudo aptitude install linux-backports-modules-intrepid-generic
```

Instead of ```
sudo apt-get install linux-backports-modules-intrepid-generic
```

Just another example of why it's so important to give a lot of info about your system when asking for help, so you can get the right answers the first time.

---

### Post by NoobBiscUiT on 2008-12-31
ok cools thanks, i have not blacklisted anything yet and i will just do ath5k when this is done :)

i will run that command also, for intrepid.

my lsusb outpus says nothing except for linux root hubs and my microdia  built in webcam.. 

it's a pci minicard, like the tiny ones.

i dont think having the antennas reversed would cause it to be invisible to the system would it? i know i have them connected right though.. although it's a n card and i only have 2 antennas on it b/c my old one just had 2.

---

### Post by 2hot6ft2 on 2008-12-31
> **NoobBiscUiT said:**
> ok cools thanks, i have not blacklisted anything yet and i will just do ath5k when this is done :)

i will run that command also, for intrepid.

my lsusb outpus says nothing except for linux root hubs and my microdia  built in webcam.. 

it's a pci minicard, like the tiny ones.

i dont think having the antennas reversed would cause it to be invisible to the system would it? i know i have them connected right though.. although it's a n card and i only have 2 antennas on it b/c my old one just had 2.
So it's a mini pci card and is internal then the lspci would be correct. It has 3 connectors making it a N-1 card. The antennas, hmmm, I don't know, but I know they're labeled to help keep you from hooking them up wrong. I've heard of problems with those. Cross your fingers.

---

### Post by NoobBiscUiT on 2008-12-31
ok so i followed all the steps and did that script, but my ifconfig output still shows nothing?..

should i do a modprobe ath_pci?
maybe that would help...?

i know i have the antennas connected right so that should not be the problem.

is there such thing as an incompatible wireless card, with my motherboard?

:confused:


these guys got it working w/ a different laptop but i dont really get how?..
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_ar5418&num=2]("http://www.phoronix.com/scan.php?page=article&item=gigabyte_ar5418&num=2")

i asked them how they did it here:
[http://www.phoronix.com/forums/showthread.php?p=57004]("http://www.phoronix.com/forums/showthread.php?p=57004")

---

### Post by NoobBiscUiT on 2008-12-31
i just followed the instructions here: [http://bbechdol.wordpress.com/2008/09/18/installing-madwifi-drivers-for-atheros-ar5418-80211abgn-on-ubuntu-hardy-heron-804/#comment-353]("http://bbechdol.wordpress.com/2008/09/18/installing-madwifi-drivers-for-atheros-ar5418-80211abgn-on-ubuntu-hardy-heron-804/#comment-353") and i get nothing after doing every step...

and i dont get why i have a red face next to this post :/


should i just switch to ubuntu 7.4?

---

### Post by NoobBiscUiT on 2009-01-12
Bump W/ edit on first post.

help please

---

### Post by frone on 2009-02-03
Next time you are in your BIOS to double-check that wireless setting, can you check the PCI slot to see if it reports the card being installed by name/model#?

---

### Post by NoobBiscUiT on 2009-02-04
i can try, 

i am in it right now and i'm not seeing anything about advanced slot information/options.

i toggled every setting under bios, like wlan control and slot enabling.

hopefully that will help recognize the card...?

any other ideas??

---

### Post by frone on 2009-02-04
Just trying to help narrow the scope of your problem.  Haven't worked on the new Mini, but just about every other recent Dell laptop seems to actually list the model number of the card installed in the miniPCI slot from the BIOS/setup.  If yours does, you can rule out your card/laptop incompatibility concerns...

---

### Post by NoobBiscUiT on 2009-02-05
I recently RE-Installed XP on the machine and then installed the absolutely correct drivers for the card, updated and everything and the computer still cant find the Gigabyte card.

if i cant find the card in xp after doing all this work, i don't think i am going to find it at all.

---

### Post by frone on 2009-02-05
Agreed.  If you have a spare or can borrow a friend's, you might want to swap out the card and see if it appears in the BIOS.  Alternatively, you could pop your card in another laptop and see if it is still not recognised...

---

### Post by NoobBiscUiT on 2009-02-05
yeah, i put the card in a friend's eee1000HD and it worked / was recognized with no problem.

this tells me that its not the card, 

when i put it in my laptop nothing happens.. at all.

dell support (through chat) has told me numerous times that they have no black/white listing of any cards in their Inspiron 910 mini.

i have tried installing madwifi in ubuntu 8.1, kubuntu 8.1, OpenSuse (newest) and nothing happens.. was recognized.

i tried multiple methods of installation in both XP and linux variations w/ nothing happening.

the BCM4312 works in the card fine though... so either somebody is lying or there is a small piece of information that i don't know that i need to.. to get this working.

my original intention was to get this thing working w/ backtrack but that wont work unless the actual computer recognizes the card.

this guy got it working somehow but is no help to me.. ([http://mini.9mods.com/index.php?topic=14.0]("http://mini.9mods.com/index.php?topic=14.0")

to be continued i guess, or im switching to a EEEpc


any ideas gladly accepted :D

---

### Post by frone on 2009-02-05
That certainly helps.  No reason to try anything under any OS until you can get the laptop to see the card.  First steps - Do you have the latest BIOS revision on the laptop?  Is there any chance the card is not seeded properly in the slot?  Do you have another card that we can try in the slot (just to rule out the slot as being faulty itself)?

---

### Post by NoobBiscUiT on 2009-02-06
Ya i just upgraded the bios.

in the (old) bios i cannot see any application or information about any system info related to the card.

The card is keyed so it really only goes in one way.

The Stock BCM4312 works fine w ubuntu and XP, but it doesn't support packet injection or monitor mode so its basically worthless, which is why i purchased the Gigabyte card.

I talked to dell for 3 hours yesterday w/ no solution to the problem :(..

i quoted a support technician saying "well what do you expect us to do" 

i was forwarded around to 14 different people, and none of them were able to do anything, even their "senior hardware technician" and their "dell mini inspiron 910 professional panel".


i am still talking to the manufacturer, but all they can really tell me is that "install drivers and it SHOULD work" and it doesn't so there's really not much they can do, bucause it sounds like a problem w/ my computer. it's not the card cuz it works fine in other laptops, and evidently its not my actual laptop because the stock BCM4312 works fine in that cardslot (mini pci) on the motherboard. 

As of right now, i have no idea.. this is just crazy.
i just want stuff to work and that's it :cry:

---

### Post by frone on 2009-02-06
I want to say 'get another card', but it worked in a friend's machine.  I want to say it's incompatible with the 910, but I've seen some threads with people accomplishing this (and your posts in them).  I want to say it's the mini-pci slot, but the original worked.  The BIOS is up to date, and you have checked all of your BIOS's wireless settings.

you have done everything you can - at this point it might be time to look into another card that supports packet injection or ask for a replacement ar5008.  Just doesn't make sense to me...

---

### Post by shaknitboss on 2009-02-06
Hi all...
I'm new here so I really don't know what I'm doing so any help would be appreciated.
I'm using ubuntu intrepid 8.1.0
Does anyone know where I can download the
madwifi-ng atheros drivers. It seems that all the
download sites no longer exist.
Also, is there a good tutorial somewhere on how to
install them once I find it.

thanks a lot
steve

---

### Post by NoobBiscUiT on 2009-02-07
Hijacking threads doesn't really get you much help.... 


Anyways!

My plan w/ this now is to just try a different card, 

The guys at Oxford.tec are letting me swap it out for a different one.

---

### Post by frone on 2009-02-09
that's good news.  Will be interested is seeing whether or not the card model# shows up in the Mini's BIOS.

---

### Post by Zeosz on 2009-04-11
That is very unusual.  I just bought that exact same card for the same reason for my dell mini 9, and it seems to be working, atleast more than yours is.  I still can't get it to connect to anything, but network manager at least shows networks and the likes.  I think your card might be faulty, but then again my card doesn't behave much better.

Sorry I'm not more technically adcanced but, I thought my experiences with the same thing might help someone who knows what to do.

---

### Post by Zeosz on 2009-06-22
After trolling around quite a bit I finally got it to work on my Dell Mini 9!

Using WICD in Ubuntu 8.10 I successfully connected to my WPA secured wireless network.  All I had to do was uninstall NetworkManager and NetworkManager-Gnome, and install WICD and it worked right away using the default Ath9k drivers. The range was abysmal, but I'm ordering a second antenna which will hopefully fix that problem.

So for the record it is possible to use a GN-WI06N-RH in a Dell Mini 9 using Ubuntu 8.10

EDIT: Range nearly doubled with a second antenna, even though it was just one I nicked from a Nintendo DS

---

