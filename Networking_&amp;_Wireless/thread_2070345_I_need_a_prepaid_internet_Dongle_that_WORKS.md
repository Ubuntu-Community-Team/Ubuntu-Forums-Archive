---
title: "I need a prepaid internet Dongle that WORKS"
date: 2012-10-12
forum: Networking &amp; Wireless
---

### Post by zacharysonicfast on 2012-10-12
I just bought a ASUS K55a notebook computer, i5, 4gb ram, 500gb hard drive.

I also bought a Cricket ZTE AC3781 USB internet dongle, a prepaid internet access.

It works without a problem with Win7 home premium, but I can't get any version of linux to even recognize that it is even connected to the computer.

The built in wifi works fine, but I am not near a hotspot most of the time.

Will there be an update or work round to get it to work with Linux??

I want to pull my win7 drive out, install an ssd drive, put win7 & Linux as a dual boot on the ssd drive, and get both to work with the dongle.

I have 2 notebooks I want to do this with and both are brand new, same brand, different model numbers.

Also, will a 64gb ssd drive do what I want??:confused:

---

### Post by grey-area on 2012-10-18
Well, I can not speak about Cricket. I have never used them. This is an older thread but it may provide some assistance:

[http://ubuntuforums.org/showthread.php?t=1146110&page=26](http://ubuntuforums.org/showthread.php?t=1146110&page=26)

What model of Asus K55A did you purchase? RBR6 from Walmart? I was thinking of purchasing that one but could find no other confirmation except your post that Ubuntu wireless works for the adapter with this system.

What version of Ubuntu are you using? Could you post the output of:


lspci -nnk | grep -iA2 net

If I can confirm you have wifi working with the same adapter,  I will be more interested in purchasing. Thanks.

I have used a T-Mobile wireless dongle in the past but it was almost 1.5 years ago. Unfortunately I no longer have access to that system so I can not tell you how I configured it to work. I am pretty sure the version I got T-Moble wireless prepaid working with was Ubuntu 11.04

Good luck

---

### Post by zacharysonicfast on 2012-10-18
Mine is an ASUS K55a running Win7 Home Premium.

Before I install any flavor of Linux I make sure it works with everything.

IMHO Ubuntu is a resource hog but Mint doesn't seem so (not capping but from experience).
I also don't like the desktop that ships with ubuntu. I want everything at the bottom.

I bought it at Best Buy.

The onboard WiFi did work for me when I tested it but the cricket dongle wasn't even recognized.

I will retest when I can get near a free wifi then post the results (wifi).

The test I did was Linux Mint 13, KDE, 64bit, an ubuntu derivative.

But I will try Ubuntu (shudders here) as son as I can.

---

### Post by Cheesemill on 2012-10-18
I think the first question we should be asking is where do you live.

Obviously different hardware and providers are available depending on which country you are in.

---

### Post by Lisiano on 2012-10-18
In my understanding of usb modems, most of them have a detachable SIM in them (Unless you are in the USA), so it could be possible (As a workaround) to grab an old phone that acts as a modem and use it with your Netbook. Old Nokias are a very good example.

What you need to do is research, make sure your next purchase is not a WinModem. WinModems are not true modems, they rely on the PCs CPU to work reliably, while true modems perform all needed operations without the help of a PCs CPU.

Also, I hear some netbooks have a SIM slot somewhere, look around, maybe you are lucky.

---

### Post by zacharysonicfast on 2012-10-19
yes, i am in the usa and they have a bad habit of locking everything so you have to PAY for each tiny little thing.

While i will see if something else is available i would like to point out that linux didn't even recognize the drive at all. Even a USB winmodem would at least be recognized even if it didn't work.

I don't want any prepaid dongle that requires my social security number and ID just to use. The problems are massively open to abuse by not only the business sector but the government as well.

Does anyone truly know who gets your info, looks at it, what they do with it and when?

Fixing an identity theft issue costs big money. I would rather steal internet somewhere than take that kind of chance.
Worst here is a slap on the wrist but most likely nothing (unless you do something illegal).

I also need prepaid to control my expenses. My credit score isn't the preferred one to get optimal credit for anything. And 30% interest rates are tantamount to loan shark rates LOL

I will D/L Ubuntu again to see if it works but have to wait till I can get to a fast broadband connection at a free hotspot if I can.

---

### Post by Lisiano on 2012-10-20
> **zacharysonicfast said:**
> Even a USB winmodem would at least be recognized even if it didn't work.Thing is, it WON'T be. It will be seen by the system as some device with no functionality, you can ask the system to use it, but the device won't tell the system what it can do.
> **zacharysonicfast said:**
> 
I will D/L Ubuntu again to see if it works but have to wait till I can get to a fast broadband connection at a free hotspot if I can.Don't, it won't help. We can try to force the stick to work but it might be not be easy.

First off, we'll need to find out what modem it actually is, so you'll have to download a tool called ScanModem. (If you don't have internet, download [this file]("http://linmodems.technion.ac.il/packages/scanModem.gz") and place it in a directory called scanModem in your home directory.)

```
mkdir ~/scanModem/
cd ~/scanModem/
wget http://linmodems.technion.ac.il/packages/scanModem.gz
gunzip scanModem.gz
chmod +x scanModem
```
Now we need to start the tool
```
sudo ./scanModem
```
Note: sudo (Not the tool) will ask for your password, type it, you won't see any kind of identification you are typing it so once you are done, press enter.
Now, scanModem created a directory called Modem, in it we will find a few files but we only need one, so open up ModemData.txt
```
kate ~/scanModem/Modem/ModemData.txt
```
(Replace kate with gedit if you are using Ubuntu instead of Kubuntu)
Now, copy paste everything in that file here inside [noparse]```
these tags
```[/noparse]

NOTE: In my opinion, it will be a lot faster (and easier) to get a modem that just-works(tm) on Linux. If possible, on your next purchase, try to "test drive" the modem and use it on your notebook before buying. Or try to get one with a SIM in it (Those almost universally work, if not, an old phone will work just as great). Or you could get one of those unlimited data plans for your phone and tether it to your notebook when you need it (Android is best in this case, preferably on 4.0/4.1 [Native support] or you might need to use AOSP/CM/MIUI/KANG [Native support] if on 2.1/2.2/2.3 [On Stock Android, might be removed by the vendor/operator])

---

### Post by zacharysonicfast on 2012-10-22
For the umteenth time I am trying to D/L Ubuntu 32 bit 12.04

I am still stuck with Win7 right now.

I went to MS tech support and they want me to call them. Problem is that my cell phone plan charges me by the minute even if the call is toll free.

I went to the ZTE web site and sent them an email. No reply yet.

If UEFI wasn't so problematic I could easily dual boot the way I want to and the problems would be far less. But once you dual boot you are stuck with both OS. I like to try out new releases. Installing and uninstalling is far too much work compared to just plugging in different flash drives when I desire.

I need a prepaid USB internet Dongle that works with anything, 3G and 4G both, Linux and Windows both.

I also need to pay cash for the monthly air time just about anywhere (no debit or credit card here). I also do NOT want to show ID or give out my social security number just for a 'cash and carry' form of internet. I would have no control over what they do with my personal information after they get it.

[https://ixquick.com/do/metasearch.pl?query=internet+dongle+that+works+with+linux](https://ixquick.com/do/metasearch.pl?query=internet+dongle+that+works+with+linux)

Not much that is available.

It seems Linux is far far behind the curve on this one.

Please note: All the Distro's I tested do work with the built in WiFi. But none of them even recognize the ZTE dongle even exists.

WiFi isn't everywhere. I wish it were.

When I take my son to the park to play, the only internet I can get is with Win7 and that Dongle.

I am no fan of windows for MANY reasons. But I am not a windows hater either.

I like Linux because it seldom if ever breaks and no real worries about malware (not dumb enuff to allow junk to run that I didn't intentionally get from the repo)

Can anyone tell me what happens if I install Linux to a flash drive then subsequently remove the flash drive when not in use?
Will windows fail to boot or force me to R/R the OS?

What if I switch to a different distro on a flash drive Do I have to install it via windows as well?

I can get by with dual booting for now. Windows & dongle when away from WiFi and Linux when hard lined or at a WiFi.

I don't use android's, palm tablets, iphones, ipads, NOOK book readers, and the like. Nearly all of them require a credit or debit card to use.

I have been debt free for 6 years now and intend on staying that way. This means no credit card or debit cards - CASH ONLY FOR ME!

Another interesting thought - what happens if I use a run from CD/DVD linux then save something to the windows hard drive. Will UEFI interfere or force a windows R/R if I do?

I cannot test anything because of UEFI. Copying Win7 C: partition requires altering existing partitions and I can't do that.

Friggin Microsoft had to screw up everything with UEFI. It is not even needed. Hard drive makers could have simply altered the hardware and everything would work just fine.

Windows could have locked the boot info to prevent anything from altering the windows boot up info and yet allow linux to dual boot as desired.

It's all about the money I suppose. And control over YOUR computer...

---

### Post by zacharysonicfast on 2012-10-22
Update: I finally got Ubuntu 12.1 or whatever the latest 32 bit version is.

It does not even show the usb dongle. Also, there is nothing in the hardware settings to actually let me look at the hardware that is connected.

I talked to the cricket dealer where I bought the dongle. He had a BAD attitude about the whole situation. He said Linux was for business apps and not very good at that! LOL

He said that almost no one uses linux. He said windows and mac were the one's that people use.

Too bad he is ignorant. MAC *IS* Linux! Just a different offshoot.
All the more reason to keep searching in earnest for a solution.

---

### Post by bra|10n on 2012-10-22
Perhaps [this]("http://ubuntuforums.org/showthread.php?t=2074518") post on my recent setup may help you...

---

### Post by Lisiano on 2012-10-24
AGAIN. Only modems that work OUT OF THE BOX are modems that use SIM cards. You could just go and buy a compatible SIM modem, then buy a prepaid SIM card with a affordable price list for data. Then use that on Linux. OR we could actually try to make that CDMA modem of yours to work. Please do what I told you to do in [my post above]("http://ubuntuforums.org/showpost.php?p=12306870&postcount=7"). I'm asking this because modems, while having the same model, might have different internal hardware (Different revisions). This is, luckily, not true for WiFi modules.

---

### Post by zacharysonicfast on 2012-10-25
Thanks, but I have a 3G version of the ZTE dongle.

My main problem is I have used PCLOS for about 3 years and nearly never had to alter files or manually make changes. PCLOS is great but doesn't work on my new laptop. I have a 64 bit i5 and the vid card is too new for them to adjust things. 

Note: I am not opposed to typing although it takes me a long time to do it but how will your information help me if I use a live version of Linux? Windows has spoiled me with the ease of use.
But it is too problematic for me - required constant babysitting with antimalware programs and constant crashing. Linux almost never crashed and isn't hampered with many of the headaches windows has.

If I were 30 years younger I probably would learn programming and make a fix for everyone. I used to love MSDOS.

I feel that Ubuntu (and other distro's) should show you exactly what is connected, where the files are, etc in the hardware section. I can find nothing in there for internet devices, especially those that don't even work.

Perhaps someone could ask the developers to put an icon in there that shows all devices?

Also, I contacted ZTE. They said to contact the ISP about divers and such.

I asked them during the email if the device was some sort of spyware or tracking device. They didn't reply to that question and merely said they code the device according to what the network provider wants and do not market to the public.

So be forewarned that something sneaky may be happening behind people's backs.

Perhaps an easy to use packet/data analyzer & logging could be of use?

Maybe that is why they won't fix it to work with linux - too easy for them to get caught?

I can't install any version of linux right now because of UEFI. When I did try it and went back to test windows, windows forced a R/R and disabled Linux. 

UEFI is very problematic. I can only use a live version of linux.

---

### Post by zacharysonicfast on 2012-11-05
> **Lisiano said:**
> AGAIN. Only modems that work OUT OF THE BOX are modems that use SIM cards. You could just go and buy a compatible SIM modem, then buy a prepaid SIM card with a affordable price list for data. Then use that on Linux. OR we could actually try to make that CDMA modem of yours to work. Please do what I told you to do in [my post above]("http://ubuntuforums.org/showpost.php?p=12306870&postcount=7"). I'm asking this because modems, while having the same model, might have different internal hardware (Different revisions). This is, luckily, not true for WiFi modules.

Unfortunately my dongle doesn't use a sim card (sigh)

Right now I am on Win7 and don't have the dongle with me (wife has it).

Note: on another post I was looking for a way to dual boot linux with windows.

I found one such way but it is a pain to do.
1st unplug the win hard drive.
2nd get an external usb drive - preferably a usb 3.0 and ssd drive)
3rd turn off or disable uefi in bios if you can.
4th install linux.
5th test
6th D/C that drive and reattach the win hard drive
7th turn the uefi in bios back on if you turned it off.
8th start the computer and windows should start like nothing ever happened.
9th shut down computer plug in the external drive
start computer and press ESC, F1,F2, or whatever key lets you choose what to boot from.

do not choose anything that says uefi on it. Some drives, especially flash drives will have a uefi listing as well as a regular listing.

Choose the external drive and the computer should work just fine.

The biggest problem I can see is people are trying to dual boot with uefi and windows as part of the setup. Anf grub interferes with uefi and windows.

As long as neither sees the other at the linux install and you manually select at boot time everything should work OK.

I did this with a USB 3.0 external drive enclosure and a 64GB ssd drive.

Speed isn't screaming but it is usable with little slow downs.

An enterprising individual might cut and splice wires installing a single pole dual throw switch to select which one before boot up

Again, I can't seem to find the post I made about dual booting. But at least it is documented somewhere (here).

Can you tell me which dongles with SIM cards are out there?
I need one that is locally obtainable and prepaid with cash.

Verizon wants full ID information which isn't needed for a prepay.

Cricket does to some degree but they aren't too picky about the ID stuff. A piece of mail with your name and address on it works for some of them.

---

