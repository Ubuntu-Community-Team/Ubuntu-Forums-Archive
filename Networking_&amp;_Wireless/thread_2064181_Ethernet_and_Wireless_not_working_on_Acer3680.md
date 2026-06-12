---
title: "Ethernet and Wireless not working on Acer3680"
date: 2012-09-28
forum: Networking &amp; Wireless
---

### Post by Kelony on 2012-09-28
Hi I am absolutely new to ubuntu. I recently decided to revive my old ACER Aspire 3680. Installation of 12.04 went well however my wireless switch does not work and neither does my ethernet and i therefore cannot activate the "Broadcom STA Wireless driver." when i try to i get 

Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log

I have listed the details of my hardware below

 03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
              Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
              Flags: fast devsel, IRQ 17
              Memory at 20600000 (32-bit, non-prefetchable) [size=16K]
              Capabilities: <access
   
  02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)


Also when i try [$ sudo apt-get update] i receive the following



  :~$ sudo apt-get update
  Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise InRelease
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                                                                                   
    
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                                                                           
    
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                                                                         
    
  Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                                                                            
    
  Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                                                                       
    
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                                                                                 
    Could not resolve 'us.archive.ubuntu.com'
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg
    Could not resolve 'us.archive.ubuntu.com'
  Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
    Could not resolve 'security.ubuntu.com'
  Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
    Could not resolve 'extras.ubuntu.com'
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg
    Could not resolve 'us.archive.ubuntu.com'
  Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/main TranslationIndex
  Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted TranslationIndex
  Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/main Translation-en_US
  Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/main Translation-en
  Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted Translation-en_US
  Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted Translation-en
  Reading package lists... Done
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise/InRelease)  
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease)  
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease)  
   
  W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease](http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease)  
   
  W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/InRelease](http://extras.ubuntu.com/ubuntu/dists/precise/InRelease)  
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
   
  W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
   
  W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Could not resolve 'extras.ubuntu.com'
   
  W: Some index files failed to download. They have been ignored, or old ones used instead.
  W: Duplicate sources.list entry cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.1%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20i386%20(20120817.3)_dists_precise_main_binary-i386_Packages)
  W: Duplicate sources.list entry cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04.1%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20i386%20(20120817.3)_dists_precise_restricted_binary-i386_Packages)


Some help would be really appreciated! Thanks

---

### Post by cbanakis on 2012-09-29
When you say your wireless switch and Ethernet don&#8217;t work, do you mean Ubuntu did not detect and install them?

Or are you talking about your actual network equipment? (outside of your computer)

Sorry if its a stupid question, but I haven&#8217;t heard it phrased like that before, hence my confusion.


Assuming your saying Ubuntu did not detect your wifi, and Ethernet cards...

I believe you can find the driver, and put on a flash drive to load on the computer in question.

I think this may be the driver you need.
[http://packages.ubuntu.com/lucid/all/broadcom-sta-common/download](http://packages.ubuntu.com/lucid/all/broadcom-sta-common/download)

Not sure though.

I'm still a little new myself.

I am usually quite lazy in situations like this, and since I always have plenty of junk laying around...

If Ubuntu does not detect my network card, I just dig through boxes, and add network cards till one works.

Then I do software updates to get the one in the computer working, then I remove the card I added.

Pretty crude, but effective, if you have the parts laying around.

---

### Post by cbanakis on 2012-09-29
Also, welcome to Ubuntu.

Not sure if your specifically new to Ubuntu, or Linux in general.

I was a Windows guy up until a couple years ago.

Some general experience I can share with you...

When I first started with Ubuntu, it was FRUSTRATING.

Its typically pretty straight forward, but on occasion, all your hardware is not detected out of the box.  (Thats where it can get complicated)

But little by little, you pick it up, and people in these forums help allot.

In my opinion, there were definitely some bumps in the road, and some hair pulling.

But after a few months of tinkering, it was all worth it.

Linux in general is great.  There are a lot of really nice distro's out there, and I definitely recommend Ubuntu for beginners, if not for everyone.

Another recommendation.  (If you want to pick it up fast)

A lot of people put Ubuntu on an extra older box they have lying around, as you are.
(Or setup a dual boot)

Not that its a bad idea, but for me, doing that got me no where.

The problem is that whenever you cant figure something out, its real easy to just go onto your main computer, and learn nothing.

If your computer is not super critical, and all your important files are backed up, I think its best to just dive right in.
(Format your main computer, and install Ubuntu all by itself)

That is just based on my experience though.

Don't do anything you can't undo, or might regret.

---

### Post by Kelony on 2012-09-29
Sorry I didnt make it clearer. I have never used linux or any of its products before this is my first go around so everything, and I mean everything is new to me. And I basically did what you did. It's an old computer and I have others that I need. I just wanted to learn about linux, sort of a hobby if you will. I erased the entire drive and installed ubuntu. it seems to work fine, except that it wont connect to my ethernet, and the switch that turns on my wireless on the computer doesnt seem to work either.

---

### Post by Kelony on 2012-09-29
> **cbanakis said:**
> When you say your wireless switch and Ethernet don’t work, do you mean Ubuntu did not detect and install them?

Or are you talking about your actual network equipment? (outside of your computer)

Sorry if its a stupid question, but I haven’t heard it phrased like that before, hence my confusion.


Assuming your saying Ubuntu did not detect your wifi, and Ethernet cards...

I believe you can find the driver, and put on a flash drive to load on the computer in question.

I think this may be the driver you need.
[http://packages.ubuntu.com/lucid/all/broadcom-sta-common/download](http://packages.ubuntu.com/lucid/all/broadcom-sta-common/download)

Not sure though.

I'm still a little new myself.

I am usually quite lazy in situations like this, and since I always have plenty of junk laying around...

If Ubuntu does not detect my network card, I just dig through boxes, and add network cards till one works.

Then I do software updates to get the one in the computer working, then I remove the card I added.

Pretty crude, but effective, if you have the parts laying around.


Sorry that was poorly written. I meant the ethernet card was not being detected and the switch on my laptop for the wireless no longer functions upon installation of ubuntu. a lot of the solutions I have found on discussion boards require internet access but i dont have that so it's quite frustrating. But i will give your recommendation a shot.

---

### Post by cbanakis on 2012-09-29
Ah, 1 thing you can try...

Ubuntu might detect the wireless, if it were on.

Then updates might fix the ethernet.

You can try turning your wireless on in your computers BIOS.

If you have no idea what that is...

When you first turn your computer on, it should say "Press (X) Key to enter setup"

X usually = F2, Del, Esc, F12...

Depends on your computer, but it will tell you which key to press.

You might have to turn it off and on a couple times, till your able to make out which key.
(Some computers don't give you a lot of time)

Once in BIOS, be very careful not to change any settings, unless you know exactly what your doing.

Cycle through all the categories, and look for enable wifi, or something along those lines.

It should be obvious which setting is for turning it on.
If its not clearly there to turn wifi on, don't mess with it.

Exit and save changes.

Once Ubuntu boots up, hopefully the wifi will be working.

With any luck, updates will get your ethernet, and your wifi switch working.

Sometimes there is no option to enable wifi in the BIOS, but usually if there is a switch, there is also an option in BIOS.

---

### Post by AndyOpie150 on 2012-09-29
You will need to install all of these packages in the order their posted:

ndiswrapper-common_1.57-1ubuntu1_all.deb
ndiswrapper-utils-1.9_1.57-1ubuntu1_i386.deb
libglade2-0_2.6.4-1ubuntu1_i386.deb
python-glade2_2.24.0-3_i386.deb
ndisgtk_0.8.5-1_i386.deb
dkms_2.2.0.3-1ubuntu3_all.deb
ndiswrapper-dkms_1.57-1ubuntu1_all.deb

I will let a Moderator know you need to move this thread to the Networking and Wireless forum so the experts can hook you right up.

You should read the sticky and make sure you post all the info necessary so they can quickly determine what you will need to do.

---

### Post by Kelony on 2012-10-24
> **AndyOpie150 said:**
> You will need to install all of these packages in the order their posted:

ndiswrapper-common_1.57-1ubuntu1_all.deb
ndiswrapper-utils-1.9_1.57-1ubuntu1_i386.deb
libglade2-0_2.6.4-1ubuntu1_i386.deb
python-glade2_2.24.0-3_i386.deb
ndisgtk_0.8.5-1_i386.deb
dkms_2.2.0.3-1ubuntu3_all.deb
ndiswrapper-dkms_1.57-1ubuntu1_all.deb

I will let a Moderator know you need to move this thread to the Networking and Wireless forum so the experts can hook you right up.

You should read the sticky and make sure you post all the info necessary so they can quickly determine what you will need to do.



Thank you very much. I will do that

---

