---
title: "3Dfx Graphics Card - Dosen't Work... Please help!"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by seamonster on 2007-10-30
Hello, I've used Ubuntu now for about 1 or 2 years. Now I've found a Graphics Card I want to use. my computer is lika 6 years old so it isn't the fastest (Infact it's a Celeron 733Mhz and 256mb Memory) 
The built-in graphics card work just fine with Ubuntu and I like it. Well, I've started to play Unreal Torunament now again (:P) and it just go up to Max 17FPS.. I've found my 3Dfx Voodoo 3 graphics card today and putted it in my computer. My brother use Windows 2k (grr) so I fixed and installed it there first. The drivers worked fine and we got a nice and smooth desktop.
So, then it's my turn :P I rebooted the computer and started it in Ubnuntu.. At the first sight it was fantastic.. well I did just se the Start-Up Loading screen.. Then it "Crashed". It came a blue/red/gray screen which said that it could not start my X-Window system (Gnome and Xfce4) Then it asked me if I wanted to see the details.. Okey.. well It didn't said much to me.. :(
Then at last.. it said: It's most likley that your X-Windows is not set up correctly (probly Gfx drivers i tought) Please restart GCM (It think it was those letters)  when you've corrected the problem.. 

It started OK in recoverymode but I dont know how to set my Gfx up in the Console!
So.. I've ripped the card out and rebooted.. Now it started in Gnome, and I looked trough the Settings and found nothing that was familiar to GFX. 

Then I opened the Ubuntu help and typed 3Dfx. It came up with a driver called "tdfx" 
Probobly it's that I need to get Ubuntu work with my Gfx. I did opned the Consle and typed:
>Sudo su
 >*****
>apt-get install tdfx

It didnt find anything.. so here I am.. Can someone please help me? I would me very greatful :D Thanks very much!

/Seamonster
PS. Sorry if my english wasnt so super good.. I'm from sweden xD DS.

---

### Post by lupin492 on 2008-01-24
Hi! Try 'xserver-xorg-video-tdfx' for the name of the package, or just look for 'tdfx' in your GUI packet-manager.
You will also need 'libglide3' to be able to get OpenGL working, and to set your xserver at no-more than 1024x768/16bits.
Good luck! :)

---

