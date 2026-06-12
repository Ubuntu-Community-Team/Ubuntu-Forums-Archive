---
title: "I'm a Ubuntu Idiot, but want to learn"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by herdoc2005 on 2009-11-07
Sorry for posting such a ignorant post...but here is my issue...
 
I have a Acer Aspire 5000. I recently loaded Ubuntu 9.1 so I can get on the "Ubuntu Craze wagon!". I love the possibilities...but have to admit I dont have a clue about anything Linux. 
 
I will be spending alot of time reading up, and learning by error. BUT I need to get my computer back on the internet to do that...I am using an extra one for now...but cant get mine working, becuase the wireless wont come up!
 
Key points that stand out to me are:
-Acer has a lil button on the front for wireless, that lights up when on, and it wont light up!
-When I do a ifconfig, it doesnt show the wlan0 interface
-when I do a iwconfig it shows it, but no access point associated
-when I do a lshw -C network it shows that the product is BCM4318 and " *-network DISABLED"
 
I have googled and found lots of stuff, but I cant get jack to work. even when I tried to use ndiswrapper it said something about not being installed...
 
What was bad though, is that I got Ubuntu up and working no problem through VMWARE on my vista box, but now that I am trying to install Ubuntu as my primary OS on my computer...POW problems! LOL But I guess thats the joy of learning something new!
 
Help getting this thing going in the right direction would be greatly appreciated! 
 
Thanks again

---

### Post by tripolitan on 2009-11-07
You might want to check the search utility of this forum (top right corner) . This is probably the most common problem facing new users.

---

### Post by pastalavista on 2009-11-07
The driver you need to install is 'b43-fwcutter' for your wireless card. If you can connect with a wired ethernet connection, run 'Synaptic Package Manager' from the System-> Administration menu and search for b43-fwcutter and install. Then from the same Admin menu run 'Hardware Drivers' and it will install and activate it and wireless should work thereafter.

If you can't get a wired connection for some reason, you can download it [HERE]("http://packages.ubuntu.com/karmic/b43-fwcutter") with your Windows box and transfer it to Ubuntu by usb-flash or cd-r

---

### Post by herdoc2005 on 2009-11-07
> **pastalavista said:**
> The driver you need to install is 'b43-fwcutter' for your wireless card. If you can connect with a wired ethernet connection, run 'Synaptic Package Manager' from the System-> Administration menu and search for b43-fwcutter and install. Then from the same Admin menu run 'Hardware Drivers' and it will install and activate it and wireless should work thereafter.
 
If you can't get a wired connection for some reason, you can download it [HERE]("http://packages.ubuntu.com/karmic/b43-fwcutter") with your Windows box and transfer it to Ubuntu by usb-flash or cd-r
 
 
I really appreciate the help...
 
But agian, I'm brand new at this..and after I go to the web site, download the firmware, and then move it over to the ubuntu machine...how do I load it???
 
I Feel like I'm typing blind with my elbows with this system right now...LOL
 
thanks again

---

### Post by pastalavista on 2009-11-07
.deb files are auto-loaders.. just double-click on it :)

Welcome to Ubuntu. There's a bit of a learning curve but it's no more that you had with Windows or Mac.. and, I think, much better support and a lot more flexibility.

---

### Post by herdoc2005 on 2009-11-07
> **pastalavista said:**
> .deb files are auto-loaders.. just double-click on it :)
 
Welcome to Ubuntu. There's a bit of a learning curve but it's no more that you had with Windows or Mac.. and, I think, much better support and a lot more flexibility.
 
hahahaha...damn I feel stupid..all the times I kept trying the whole double click and not get any luck...and this time I elected on asking before...go figure!
 
thanks again bro...hopefully this works...

---

### Post by motoperpetuo on 2009-11-07
i hope you stick with ubuntu and linux. it will probably be frustrating for a while, but once you get comfortable with it, you'll probably prefer it to windows and the proprietary software world. i got rid of my last windows computer about a year ago and went pure linux, and it's great. even if i get occasional things like comcast telling me that linux is "not supported" (no problem, i got it to work anyway).

---

### Post by herdoc2005 on 2009-11-08
> **motoperpetuo said:**
> i hope you stick with ubuntu and linux. it will probably be frustrating for a while, but once you get comfortable with it, you'll probably prefer it to windows and the proprietary software world. i got rid of my last windows computer about a year ago and went pure linux, and it's great. even if i get occasional things like comcast telling me that linux is "not supported" (no problem, i got it to work anyway).
 
Thanks brother, thats kinda the goal.  I work with networking equipment alot, so I figure if I like CLI with Cisco's IOS, then why not take a lil more time and learn a few things about Linux, that could benefit so much more!
 
It is a learning curve, and I have alot of bad practices with what I do with work...but I'll slowly make progress!

---

### Post by herdoc2005 on 2009-11-08
Well so far, I have downloaded the driver, as well as try the ndiswrapper route...and the only thing it has gotten me so far, (besides a bunch of typing) is now my wlan0 interface is not even recognized at all... So, becuase it would take me longer to figure out what I did wrong...going with a fresh install, and goign to start again :)
 
This is going to be a story that everybody here can come and get their daily laughs :)

---

### Post by herdoc2005 on 2009-11-08
I tried the steps right off of:
 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
 
But once I got to step 3 of "witout internet access"  that is where my eyes start crossing, and I'm a bit confused when things dont work out, becuase I am suppose to change the typing a bit...
 
But, when I do a lsmod | grep b43, I get stuff...but nothing still on ifconfig?  
 
oh...the joy HA

---

### Post by herdoc2005 on 2009-11-08
Then I tried to do all the steps on:
 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Identifying](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Identifying) Wireless Adapter
 
and...this is where I dont have anything on iwconfig anymore...as well as anything up on the top where the lil network connection is supposed to be...doesnt say wireless anything anymore...
 
So, I'm goign to try to put it back to the other firmware, and not the ndiswrapper windows driver...
 
oh yea...also when I did do the wireless network driers and install the driver...it said "unable to see if hardware is present"???

---

### Post by herdoc2005 on 2009-11-14
Well I think I have figurd out what the problem is.  I dont seem to have the acerhk file loaded...
 
so I went and foun the acerhk-source_0.5.35-3_all.deb file.  
 
But when I try toload it, I get a 
error: dependency is not satisfiable: debhelper (>=5)
 
So...my issues are that I cant get onto a ethernet nework to download anything the easy way...
 
I dont think that network manager is loaded, and now acerhk-source as well...
 
I think once I figure out how to get these working, I'll be up on the net!!!!
 
help would be great!

---

