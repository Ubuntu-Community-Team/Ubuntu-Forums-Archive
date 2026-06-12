---
title: "Belkin N+ router USB storage"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by bobby159 on 2010-06-03
So I have a belkin n + router and it has the feature of plugging in a flash drive and making it accessible to everyone on the network. Like a NAS. It says to connect to it by using the file browser and typing //192.168.2.1/nameofdevice where that is the name of the flash drive or whatever it is. I tried that and that didn't work. its name is KINGSTON. So I tried to browse for it in nautilus and found the folder which then asks for a password. there is no password. even to get into the router. I have no idea how to get to it. Any ideas? Thanks in advance, John.

---

### Post by Blacksheep01 on 2010-07-05
Bump as I have this same problem. I have a Belkin N+ router with a 320GB Toshiba portable hard drive plugged in via USB to the router. Now, my router does have a password and I also have a WPA2 password. When I attempt to connect to the hard drive that is attached to the Belkin Router (via places - network-windows network- Belkin- Belkin N+ -Toshiba Ext), I get a window that pops up and indicates I need a password to access "toshiba ext on Belkin N+"

The form starts with "username" and auto fills it with the name of this Ubuntu PC. It sets the domain to "workgroup" and asks me for a password. I have tried both my routers passwords to no avail. I have then tried to change the "username" portion to my routers SSID, the only thing I haven't messed with is domain yet I am still not able to access the HD. Thing is, on my other Windows based PCs, I can access this hard drive without entering a password at all.

So, what do I need to be able to do to access this hard drive that is attached to the router? I suspect the answer would help the OP also. 

Thanks

---

### Post by EddieNYC on 2010-07-08
Bump as I have the exact same problem with my Belkin N+ router with a Seagate 1TB HD connected to it. Also asks me for a PW but is not pw protected and can be accessed without restrictions in Windows.

---

### Post by Jeepman on 2010-08-02
This is retarded, We all have the same issue and Belkin is ok with helping Windows and The Mac but when it comes to its Ubuntu users we are out with the Wolves. I am Have the same issue as all of you and it is getting me vary angry, I should turn Green sometime soon and go after Belkin.

---

### Post by dmurphy787 on 2010-08-06
I have the exact same issue, except I have a 1.5tb drive.  We need to pool our resources and be patient for a solution

---

### Post by dmurphy787 on 2010-08-10
Here is how I did it:
Access &#8220;Places&#8221;  &#8220;Connect to Server&#8221; &#8220;Windows Share&#8221; 
Enter &#8220;192.168.2.1&#8221; into &#8220;Server&#8221; area and click &#8220;Connect&#8221;
or SMB//192.168.2.1 in address bar of browser.
The drive will be listed, click on it and enter the following in the fields shown.
Username: guest
Workgroup: Belkin
password: leave it empty
Remember authorization forever. And now it works.
:KS:D:D:KS

---

### Post by Blacksheep01 on 2010-08-21
> **dmurphy787 said:**
> Here is how I did it:
Access “Places”  “Connect to Server” “Windows Share” 
Enter “192.168.2.1” into “Server” area and click “Connect”
or SMB//192.168.2.1 in address bar of browser.
The drive will be listed, click on it and enter the following in the fields shown.
Username: guest
Workgroup: Belkin
password: leave it empty
Remember authorization forever. And now it works.
:KS:D:D:KS

You Sir, are my new hero! That worked flawlessly, only thing to add was after I did all that I had to type in my system's overall pw, but I did and it worked, now I can get on my files on this here Ubuntu box. Thanks so much, I now have every single thing working properly in Ubuntu, so excited!!!!!!!!! :guitar:

---

### Post by dmurphy787 on 2010-08-21
Thank you for your reply, I am very pleased to hear of another happy Linux family member.  I to am only a new user but I have thought about it for about 20 years and never got to do. I am very happy and excited to be using this fantastic system.
Keep the system functioning by sharing your knowledge with others and we can all enjoy.   :p:D

---

### Post by maryyeta on 2010-08-25
Thank you very much!

---

### Post by dmurphy787 on 2010-08-26
:popcorn::p:p:D:D

---

### Post by LinuxTime on 2010-08-31
Thanks!

---

### Post by adpads on 2010-09-14
I hope you guys can see what my stupid mistake is... 
I have a Belkin Double N+ router, and this solution isn't working for me. I have set the SSID to something different, and changed the domain name in the router settings. Somehow I've tried all the combinations of Belkin, the name of the drive, the SSID of the network, and the passwords to the router, everything I can think of, but no joy.
Anyone else have this router? Is it different from the Belkin N+?

---

### Post by dmurphy787 on 2010-09-14
HI,
When I encounter these sorts of problems, I first eliminate all other possible problems.  You said that you have changed the router setting to have a different domain name and perhaps some other things.  I would recommend resetting the router to its default state, reset up your security and do nothing else.

Then follow these instructions and see how you go.
Access “Places” “Connect to Server” “Windows Share” 
Enter “192.168.2.1” into “Server” area and click “Connect”
The drive should be listed, click on it and enter the following in the fields shown (Please don't be tempted to change anynames or groups as these are the defaults).
Username: guest
Workgroup: Belkin
password: leave it empty "Do not put any characters here"
Remember to click "authorization forever" and now it should work.

---

### Post by aldolen on 2010-09-20
Hi!

I'm more or less in the same situation, i.e. I just bought aan brand new Belkin N300 Play router, I use ubuntu 10.04 for netbook and I can use the way posted before to reach my usb disk on the router.

But. But when I try to look inside the disk, there's nothing. And I assure you I have a bunch of useless things on this disk (and some of them may not be totally useless). 
Moreover, I can't create a folder or move anything to the blank space supposed to be my disk...

Anyone has any clue for a solution?

By the way, thanks to blacksheep for sharing the info...

---

### Post by dmurphy787 on 2010-09-20
Here is how I did it:
Access “Places” “Connect to Server” “Windows Share” 
Enter “192.168.2.1” into “Server” area and click “Connect”
or SMB//192.168.2.1 in address bar of browser.
The drive will be listed, click on it and enter the following in the fields shown.
Username: guest
Workgroup: Belkin
password: leave it empty
Remember authorization forever. And now it works.

---

### Post by aldolen on 2010-09-21
Yip... I read that this worked for you, and it almost worked for me...

My question is, anyone has an explanation about my disk appearing empty an unwritable?

---

### Post by dmurphy787 on 2010-09-21
This may not be the correct thread for this answer, I suggest you create another Post specifically about your error.  I think the answer to your question lies in the fact about the mounting of your drive and you need to perhaps look for similar threads along those lines.  Sorry I can't help further.

---

### Post by shaon.scb on 2011-01-05
Hi,

I'm facing issues accessing Belkin N+ storage share from my WD TV LIVE media player. I think this is because the default name of share (Belkin N+). How can I change the name of that? Any idea?

Thanks,
Shaon

---

### Post by smulle on 2011-02-08
> **shaon.scb said:**
> Hi,

I'm facing issues accessing Belkin N+ storage share from my WD TV LIVE media player. I think this is because the default name of share (Belkin N+). How can I change the name of that? Any idea?

Thanks,
Shaon

Found this on DD-WRT forum [http://www.dd-wrt.com/phpBB2/viewtopic.php?p=529683](http://www.dd-wrt.com/phpBB2/viewtopic.php?p=529683)

To change your router name and workgroup you have to go to hiden page on your router. I found it somewhere on internet. Here it is:
[http://ROUTER_IP/util_storage_admin.htm](http://ROUTER_IP/util_storage_admin.htm)

---

### Post by donovan.thompson on 2011-03-07
Just wanted to add my thnaks because you probably saved me hours or searching and finding an answer as I see many others have...

---

### Post by rikib on 2011-05-05
> **dmurphy787 said:**
> Here is how I did it:
Access “Places”  “Connect to Server” “Windows Share” 
Enter “192.168.2.1” into “Server” area and click “Connect”
or SMB//192.168.2.1 in address bar of browser.
The drive will be listed, click on it and enter the following in the fields shown.
Username: guest
Workgroup: Belkin
password: leave it empty
Remember authorization forever. And now it works.
:KS:D:D:KS


Mate, you are a savour of all sanity......I was going utterly barmy trying to figure this out!  Thank you!

Riki:popcorn:

---

### Post by DaveAB6 on 2011-09-12
Originally Posted by **dmurphy787** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9704025#post9704025") 				
 				[I]Here is how I did it:
Access “Places”  “Connect to Server” “Windows Share” 
Enter “192.168.2.1” into “Server” area and click “Connect”
or SMB//192.168.2.1 in address bar of browser.
The drive will be listed, click on it and enter the following in the fields shown.
Username: guest
Workgroup: Belkin
password: leave it empty
Remember authorization forever. And now it works.
:KS:grin::grin::KS

I'll Try this when I get home tonight, haven't been able to connect to this or my Win 7 shares at all.  Hope this works!  Thanks in advance!
[/I]

---

### Post by h4ck3rc1 on 2012-04-25
Anyone having trouble accessing USB devices connected to your router, just an update on the thread.
For Belkin PlayMax router using Ubuntu 11.10:

Go in to Nautilus and then File menu > Connect to server.
In the dialog box, choose Windows Share from the drop down then enter the following,
192.168.2.1 in to the "Server" text box
Leave "Share" blank
"Folder" should have a "/" by default, leave it there
Under "Domain name" type "Belkin"
"Username" is guest
and leave password field blank

Nautilus should then open up and list your connected devices :)

Note: I had trouble at first because I had connected my hard drive directly to a USB port on my computer and pulled it out without un-mounting it. I found it would not show up in the list, nor would the USB light on the back of the router light up until I plugged it back in the computer and then un-mounted it in Nautilus.

Edit: I am using Ubuntu 11.10 x64, connecting a Seagate 1TB desktop drive via USB on Belkin PlayMax Model: F7D4401 v1.
Computer: Core i5 2500K, ASUS P8P67-LE, 8GB Corsair Vengeance, 1TB internal WD Caviar Black, GeForce GTX 260+

---

### Post by h4ck3rc1 on 2012-04-25
As an observation after using it for a while, I notice the once the drive spins down for it's automatic power saving; it can cause it to disconnect, in which case you may have to close nautilus and re-open the drive.
It should save in the left column under Network down the bottom automatically, I also added it to bookmarks for easy access.

---

### Post by danauber on 2013-02-07
Hi I have a Belkin N+ with storage. It works fine for a while, but then after a couple of hours it switches off - the blue storage light goes out and the drive is no longer available. Any ideas very welcome.....I think it might be the drive powering down - but if it is I don't know if there's a way to stop it happening ?
 
Thanks for any help out there 
 
Dan

---

