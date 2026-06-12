---
title: "Can't Open Linksys Install Disc"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by Uadebisi on 2009-12-19
Hi,

This seems like a rather simple issue but I am stumped. I was using a Linksys router which was set-up with my Windows systems prior to my installing Ubuntu. When I removed Windows & installed Ubuntu, the internet connection always just worked. I was using a wired connection only.

I have a new laptop coming so I picked up a wireless Linksys router & am beginning to set it up. This will not be a network set-up but rather machines simply using the router as an internet connection. There will be one Ubuntu desktop & one Windows desktop which will both be hard wired & one Mac laptop to which I will set-up a wireless connection.

However, I cannot even open/load the Linksys install disc on my Ubuntu machine! My CD drive works fine otherwise. What to do? The CD is briefly recognised & then the drive disappears from the CD File Browser or sometimes remains but nothing happens when I try to open it.  Any help would be appreciated. Thanks.

---

### Post by yelvington on 2009-12-19
You shouldn't need an installation disk. (I would not use one even if I were running Windows.) 

Just plug the router in, turn it on, connect your Ubuntu desktop using an Ethernet cable, and browse to the router's address (usually 192.168.0.1). Log in using the username/password provided in the manual, and configure it using the Web interface.

Since this is your first time using a wi-fi router, PLEASE be careful to:

* Change the router's name
* Configure WPA encryption using a decent passphrase
* Change the administrative password (different from the encryption passphrase)

---

### Post by coffeecat on 2009-12-19
I think you'll find this "Linksys install disc" is just a Windows setup wizard. Like the last poster, I wouldn't touch it with a 50-ft bargepole. All you need to do is log in to the router configuration web-interface using Firefox. I have an old Linksys router and the log in address is 192.168.1.1 rather than 192.160.0.1, but you'd better check the manual to be sure.

Trouble is, the manual is probably on that CD in PDF format. All the device manufacturers seem to be saving paper at the moment. If you can't get the CD to open on your Ubuntu machine, can you get the PDF off using your Mac?

---

### Post by Uadebisi on 2009-12-19
Thanks!
> 
I think you'll find this "Linksys install disc" is just a Windows setup wizard.

You are correct :)

> wouldn't touch it with a 50-ft bargepole.

Correct again! What a pain in the neck! I ran it on my Windows machine & it wants to & does, install other software that I do not need. Now that I've cleaned up that mess, I think I'm good again.

I'll connect the new Mac w/o the cd & however the user manual in on the disc so, if I really need it, I can open it with my Windows machine.

Thanks again!

---

### Post by Thocrun on 2009-12-19
> **coffeecat said:**
> I think you'll find this "Linksys install disc" is just a Windows setup wizard. Like the last poster, I wouldn't touch it with a 50-ft bargepole. All you need to do is log in to the router configuration web-interface using Firefox. I have an old Linksys router and the log in address is 192.168.1.1 rather than 192.160.0.1, but you'd better check the manual to be sure.

Trouble is, the manual is probably on that CD in PDF format. All the device manufacturers seem to be saving paper at the moment. If you can't get the CD to open on your Ubuntu machine, can you get the PDF off using your Mac?
  There probably is a .pdf in it somewhere that shows how to do an advanced setup (which you probably want to do to enable most of the security features that came with your router(if any))

---

### Post by Uadebisi on 2009-12-20
[quote=yelvington;8527582]You shouldn't need an installation disk. (I would not use one even if I were running Windows.) 

Just plug the router in, turn it on, connect your Ubuntu desktop using an Ethernet cable, and browse to the router's address (usually 192.168.0.1). Log in using the username/password provided in the manual, and configure it using the Web interface.

Thanks yelvington, but this does pose a question. Seems that the only way to change or edit the user name is via the disc. Hmmm...any thoughts? 

BTW, I spent many, many hours trying to remove all of the crap that Cisco installed vis CD. I figured I would have a chance to choose what I wanted to load & what I didn't...I was very wrong. "Cisco Network Magic" doesn't fully uninstall via add/remove pragrams & I had one heck of a time getting rid of everything. I think I finally did. 

Not putting that disc in my new Mac!

---

### Post by coffeecat on 2009-12-20
> **Uadebisi said:**
> Seems that the only way to change or edit the user name is via the disc. Hmmm...any thoughts?

That's not so. The answer is in the manual! Open Firefox, or any web browser (in **any** OS) and type 192.168.1.1 in the address bar. I think you'll find the gateway address for Linksys routers is 192.168.1.1, **not** 192.168.0.1, but as I said before check the manual. So long as you are connected to the router, you'll be prompted for your router admin username and password. For my Linksys router, the defaults were 'admin' and 'admin'. :rolleyes:. You'll almost certainly find it's the same for your Linksys, but check the manual.

Once you're into the web interface, click on the administration tab and change them to something more intelligent. You'll see a number of tabs for all the functions. It's all fairly easy to get around.

---

### Post by Uadebisi on 2009-12-20
> **coffeecat said:**
> That's not so. The answer is in the manual! Open Firefox, or any web browser (in **any** OS) and type 192.168.1.1 in the address bar. I think you'll find the gateway address for Linksys routers is 192.168.1.1, **not** 192.168.0.1, but as I said before check the manual. So long as you are connected to the router, you'll be prompted for your router admin username and password. For my Linksys router, the defaults were 'admin' and 'admin'. :rolleyes:. You'll almost certainly find it's the same for your Linksys, but check the manual.

Once you're into the web interface, click on the administration tab and change them to something more intelligent. You'll see a number of tabs for all the functions. It's all fairly easy to get around.

Hi coffeecat,

I do know how to get around the router however, I cannot find where to change the wireless connection name. I just looked again & all that I can change in the admin section is the password. In the wireless tab, I can also change the passphrase for the wireless connect, but that seems to be it. I have been thru the tabs countless times. I was hoping that I was missing something.... :confused:

---

### Post by coffeecat on 2009-12-20
Hoping that Linksys configuration interfaces are much of a muchness, here is where is you find what you want with what I can see in my Linksys interface.

Log in and you should default to the Setup and Basic setup page. There are two sets of tabs, one above the other. In mine, while you're in the basic setup page, the upper set of tabs shows: Setup | Wireless | Access Restrictions | Applications and Gaming | Administration | Status. The lower set of tabs shows: Basic Setup | DDNS | Advanced Routing. Yours might be a little different, but click on the 'Wireless' tab (upper set) and the lower set should now show: Basic Wireless Settings | Wireless security | Wireless Access | Advanced Wireless Settings.

For the connection name you need the Basic Wireless Settings tab, not the Wireless security one. The field you want is 'Wireless Network Name (SSID)'.

---

### Post by Uadebisi on 2009-12-21
coffeecat,

Boy do I feel a bit dumberer

I am aware of all of the various levels of tabs, however....

I was failing to change the Wi-Fi set-up to manual configuration in the Wireless- Basics tab. Ya see, with Wi-Fi Protected Set-up enabled, I was only able to see the wireless connection name but when I ticked the manual box, it was there, that I was able to make the change. 

On another note, I didn't even need to click on the Wi-Fi Protected Set-up icon, as suggested by Linksys, to set-up a connection with my new laptop. Apple automatically set it up. I only needed to enter a password on the Mac to form the connection.

Thanks for sticking with me!

Merry Christmas & Happy New Year

---

