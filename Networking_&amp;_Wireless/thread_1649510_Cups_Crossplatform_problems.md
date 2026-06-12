---
title: "Cups Crossplatform problems"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by whiteman on 2010-12-20
OK. It all started when I couldnt really use Jaunty anymore. Everytime I tried to upgrade..I lost my Canon prtr. The add/prtr only showed my HP, Network, and other.
So I just kept installing, partitioning reinstalling. Finally decided to stop with 10.4. NOW I have two wired desktops..Ubuntu(has all the prtrs attached) The Windows7, in the same room(ethernet) Using dlink 655.
My Pavilion and my Macbook connected wireless. When I try to share files with MBP I have to choose recent files in order to locate now. When I go to add printers there is no server or workgroup listed undr windoze category. 
I finally got the Canon(most desireable printer) installed with Turboprint. That was the only way that Ubuntu would SEE this printer. Otherwise it remained invisible, hence I couldnt install. I had loads of drivers listed under my Gutenprints..but couldnt make them "stick" unless I could first see the usb connection. Turbo allowed for this. SO now Im happy camper..right?
Not quite.
The macbook allows me to install the canon for cup printing but in an odd way. It s shown under DEFAULT instead of under Windows...with the browser style.(It used to show my server...workgroup...and then the two printers. Now it shows nothing under this.
I think its a Netbios thing?
Also when I use cups:631 website..I cant make changes. It wont acccept my password.(Itwill on the wired Ubuntu) 
I didnt have to do anything fancy before. I didnt edit any config files except smb.conf where I entered workgroup name.
I have used sudo enabled Nautilus to provide sharing and doubled up with the Samba gui.
My File System folder is Root root. My two externals are owned by me.
So Why the authorization problem? I am able to share files and print wirelessly from the mac and the win laptop. Also from the wired win7. BUT it aint elegant! And I have a feeling that if I upgrade from within 10.04..it will all go away. Then there is the Turboprint which is some kind of subscription service? I gotta pay to print from my own printer, with a gutenprint driver? And it dont even show the HP. Why is the cups not recognizing me on the wireless servers? This has never happend. I use a very simple username password combo for everything. wth....zzzzzz. respectively. So root and cups have identcal passwords ect.

---

