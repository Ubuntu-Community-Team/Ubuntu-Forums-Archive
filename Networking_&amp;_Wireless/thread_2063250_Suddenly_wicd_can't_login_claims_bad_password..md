---
title: "Suddenly wicd can't login claims bad password."
date: 2012-09-26
forum: Networking &amp; Wireless
---

### Post by jtwdyp on 2012-09-26
Well the full story would be a long sorry tale... But in it there might be some detail that I should have mentioned here. So If you want the long version read [http://pastebin.com/jewAHMtc](http://pastebin.com/jewAHMtc)

The short version is I have a gateway mt6451 notebook with a built in wireless that never worked for me with any Linux nor even the Vista that came with the laptop. So I got a usb wireless adapter which combined with wicd worked with all 5 installed Linux distros and vista to connect to my "hidden" wpa-psk network connection to my Fairpoint DSL. Now I say it worked with all the installed Linux, but for Xubuntu I couldn't turn off the ssid broadcast until I started using a bash script to specify the name of my network to wicd-cli. Which worked well until shortly after I upgraded my lucid 10.04 LTS to a precise 12.04 one with do-release-upgrade.

It actually worked for a couple of days and a half dozen reboots. But I was hoping that precise was able to remember the name of the hidden network. So I used wicd-gtk where I checked the automatic connection option box. two boots later it stopped working. Sometimes it quietly fails to connect.  sometimes it claims the password is bad. and sometimes it can't even find the network. Even when it's specified on the wicd-cli command line. And I even tried turning the SSID broadcast back on, but it didn't help...

I don't want to give up on *buntu just because I can't figure out how to make wicd work on precise...  But frankly I'm at wits end.  

[COLOR="Blue"]PS: I don't think It's my hardware because not only did the exact same config work with Lucid for over a year, but virtualy the same config still works with my other installed Linux...[/COLOR]

-- 
jtwdyp
J(tWdy)P
Joe(theWordy)Philbrook

---

