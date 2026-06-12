---
title: "Problems Setting Up Vodaphone Dongle Model #K3570-Z"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by bry72 on 2011-01-08
Hey Guys,

So here is my situation:

A relative of mine currently living in England, has a friend who's  computer wasn't working well (Windows).  She was bringing him back to  the States for the holidays and I told her to have her friend bring his  laptop along and I would install Ubuntu.  I asked in advance what type  of Internet connection they use and she said a wireless signal.

So I installed Ubuntu, set up everything to reflect a UK computer,  checked the wireless connection at a local Starbucks and I told her that  her friend now had a "new" computer.

However, she failed to inform me that they use a Vodafone dongle.  In  Windows, it takes about one minute to set up and get connected to the  internet.  We're finding out in Ubuntu, it takes quite a bit longer.  :(

I have done extensive searching throughout the threads and have read the following:
[http://ubuntuforums.org/showthread.php?t=1465557](http://ubuntuforums.org/showthread.php?t=1465557)
[http://djjlewis.wordpress.com/2010/11/07/vodafone-uk-topup-and-go-prepay-mobile-broadband-usb-dongle-on-ubuntu-10-10-netbook-edition/](http://djjlewis.wordpress.com/2010/11/07/vodafone-uk-topup-and-go-prepay-mobile-broadband-usb-dongle-on-ubuntu-10-10-netbook-edition/)
[http://ubuntuforums.org/showthread.php?t=1554716](http://ubuntuforums.org/showthread.php?t=1554716)
[http://www.jarviser.co.uk/jarviser/vodafonedongleslucid.html](http://www.jarviser.co.uk/jarviser/vodafonedongleslucid.html)

When she plugs the dongle into the usb port, it displays a flashing blue  light.  However, there is no start up wizard box that pops up.

I had her go through the steps of setting up the signal using Edit  Connections->Mobile Broadband->Add.  When she gets to the screen  "Set Up A Mobile Broadband Connection", nothing is listed underneath the  section that says, "Create a connection for this mobile broadband  device".  It simply says, "Any device" in grey and you can't click on  the drop down box.

I still had her go through all the other steps listed in the threads I  mentioned above, but no connection.  My one concern is that it is  not giving a device to select, which to me, indicates that Ubuntu hasn't  "recognized" it.

The "jarviser" website listed above mentions that he sees his device  listed in the drop down box yet he did not have to install  usb-modeswitch-data and usb-modeswitch.

I am sending her to a local Starbucks in the UK to use their WIFI signal and install usb-modeswitch-data and usb-modeswitch.

I installed Ubuntu 10.04 on his computer and he is using the Vodafone Model #K3570-Z.

I am crossing my fingers that installing the usb packages will do the  trick..

On a side note, how do I verify on her computer (Windows XP) what the APN is?  They both currently use the "TopUp and Go" plan in the UK.

If you use the mobile broadbrand wizard and choose UK and TopUp and Go,  it gives the APN as being pp.internet.  However, this APN does not work  for some (as mentioned in some of the threads listed above). In both of the links  above for the jarviser.co.uk and djjlewis.wordpress.com websites, they advise  not to choose Vodaphone and instead select the "I do not know my  provider", enter "My Vodaphone" and input PPBUNDLE.INTERNET as the APN.  I just want to make 100% sure that this is the correct APN for the TopUP and Go plan in the UK.

I also need to mention that his TopUp and Go plan has expired.  My relative said that when you install the dongle on Windows and you haven't paid for your plan, it gives a pop up box that allows you to go through with adding payment before connecting.  I just read on another thread, that Ubuntu won't allow you to do this.  Any ideas on how he can reload prior to connecting to Ubuntu?  Can this be done at a local Vodafone shop or does she have to install his dongle on her Windows XP computer, update payment and then try installing on his Ubuntu computer?

Lastly, when you get to the end of setting up the mobile broadband signal and it shows you the "Editing Vodafone TopUp and Go" box with  the three tabs: Mobile Broadband, PPP settings and IPv4 settings, there is a box near the top that says, "connect automatically".  Should this box be checked or not?

Thanks.

---

### Post by bry72 on 2011-01-09
Update: My relative went to Starbucks and they do not have "free" wifi.  You have to purchase a card that costs 5 pounds ($7.75), buy a coffee and come back in 24 hours.  That doesn't include them having to pay for parking as well. It's ridiculous because in the States, you can walk into a Starbucks and use their unsecure WIFI signal and not have to buy anything.

My assumption is that this will be a secure WIFI signal and require a username and password.  When I click on a secure WIFI signal on my computer a box pops up and says, "Authentication Required by wireless network".  It says: " Wireless security" and has a drop down box.  It defaults to: " WEP 40/128 bit key" and asks to input a key.  The only choice that allows you to enter a password is if I choose "LEAP" in the drop down box.

Has anyone ever used a Starbucks internet card in the UK?  If so, what is the process of getting logged on in Ubuntu 10.04?  Is there a time limit or do they limit the amount of data you can download?  This makes a big difference as I have instructed them to download any updates.

My relative and her friend are extremely upset at this point as they visited the Vodafone shop as well and they know nothing about Linux.  This is turning out to be a big mess and I may have to resort to having them buy a used copy of Windows XP since this guy is only familiar with it.  He doesn't know anything about computers and even though I am a newbie as far as Linux goes, I am trying my best to help them.

Anyone know of a FREE UNSECURE WIFI signal in Winchester, England (UK) that doesn't require buying a coffee, meal, item etc.?  Someplace that has an unsecure signal where he can plug his laptop into a electrical socket (his laptop battery is dead) and download these damn usb packages?

Also, they cannot pay for the "TopUP and Go" plan at the Vodafone store.  It has to be connected to the internet and paid that way.  Seeing that his plan is expired, will the dongle even connect in Ubuntu and allow him to pay?  In Windows it does this.  I read a thread that says it doesn't do this in Ubuntu.

---

### Post by bry72 on 2011-01-10
Update:  Had relative go to Starbucks and download the usb packages and Ubuntu 10.04 still won't recognize the device.

I emailed someone who posted on this forum and was able to get this particular model to connect on his computer a few months back (he has multiple dongles).  He tried it again last night and it would not work.  Ubuntu 10.04 would not recognize it.

Does anyone know of a Vodafone dongle model that works 100%, unequivocally, right now on their computer in Ubuntu 10.04 for the "TopUp and Go" plan?

Buying a model that actually works in Ubuntu 10.04 is a last resort but I need to make damn sure it actually works before I send this guy out to buy something he cannot return.

If not, they are going to have to buy a copy of Windows, which they know actually works with Vodafone dongles.

Can't believe how difficult this is in Ubuntu when it's a one minute process in Windows.:frown:

---

### Post by Linicks on 2011-01-10
There could be a gotcha here.  I have a 3internet dongle (in UK), and when first inserted, it gets mounted as a virtual cdrom drive.  You have to go to places -> eject, and then it appears in network manager as a modem, so then you proceed with configuration.

Nick

---

### Post by bry72 on 2011-01-10
Update:  I am going to mark this thread as being resolved even though the person has decided to install Windows after this mess.  I am posting the resolution in case someone else is having problems with the Vodafone Model K3570-Z in Ubuntu 10.04.

I received another email from the guy who tried installing the dongle on Unbuntu 10.04 a few months back, had it working but couldn't get it to work again last night (again, this guy has multiple dongles).  He was kind enough to take the time and try it in Ubuntu 10.10 with usb-modeswitch-data and usb-modeswitch packages installed.  He plugged the dongle in and said it took about one minute before Ubuntu recognized it.  He was then able to go through the set up wizard, pay his account online and connect to the internet.  He used  PPBUNDLE.INTERNET as the APN for the "TopUp and Go" plan.

1.  Make sure you are using Ubuntu 10.10

2.  Do a search in these forums on how to install usb-modeswitch-data and usb-modeswitch in Synaptic Package Manager (sorry, too tired to type out the instructions myself).

3.  Make sure you have the dongle plugged in for a minute or so until Ubuntu recognises it.

4.  Go to this website and follow the instructions:
[http://www.jarviser.co.uk/jarviser/vodafonedongleslucid.html](http://www.jarviser.co.uk/jarviser/vodafonedongleslucid.html)

---

### Post by hivemaster on 2011-01-13
I also purchased the K3570-Z dongle and after about 10 minutes I had it working.

However, it seems it was a mixture of things that got it working, but having said that it now works everytime under Network Manager with no issues.

The Process was as follows

##You can skip this bit##

Download sakis3g ([http://www.sakis3g.org](http://www.sakis3g.org))

Insert dongle 

run sakis3g 

note settings (when you get it working)

##DO this bit##

Setup Network Manager as follows
Mobile Broadband
Number - *99#
Username - web
Password - web

APN - PPBUNDLE.INTERNET

Tick Connect Automatically

That should do it and I hope it helps

uname -a "Linux otter 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux"

cat /etc/issue "Ubuntu 10.04.1 LTS"

H

---

