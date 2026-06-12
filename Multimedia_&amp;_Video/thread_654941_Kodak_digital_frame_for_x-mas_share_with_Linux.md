---
title: "Kodak digital frame for x-mas: share with Linux?"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by malibu on 2007-12-31
I got a Kodak (EX811) digital frame for x-mas and the thing is awesome.. It connects wireless and pulls pics off the web and even pipes music to my stereo.  The problem I'm having is that my main PC is Ubuntu here and it doesn't seem to want to share files on my network.  It shares pics from the kodak site which is fine but for my music I need to share from my main PC.  It doesn't seem to recognize normal samba shares.. I can get it to work on my Windows desktop but I have to do it through Windows Media Player 11.  There's a sharing media panel and it seems to be different then any of the other connection methods.

Does anyone know how I can do this with linux?

Thanks!

---

### Post by linuxaz on 2007-12-31
Hello,
I'm not familiar with this product so this just a guess.
Is there configuration available for the network sharing inside the frame?

I notice that most devices have their network workgroup name set to 'WORKGROUP' simply because it make it easier to work with win only networks.  If your network is named something else, or you have password enabled shares on your samba setup, you may not be able to browse easily from the picture frame.

linuxaz

---

### Post by malibu on 2007-12-31
Yeah I've been sharing stuff all over my house for a couple years now in many different ways but this one is a new one by me.  It's not a normal samba share.  First of all, they force you to 'upgrade' to WMP 11.  Then there's a menu item Library->Share Media.  It detects the picture frame on the network and you 'approve' it for sharing.  Then you can access the media in your library on the frame.  It's pretty slick, but I'm not sure why they couldn't just use normal windows shares.

Anyway, I was hoping the Ubuntu community might have a way to do this in Ubuntu.  I was just about to go 100% Ubuntu in my house but then it occured to me that my frame might not work.  Now I'm thinking I might return it.

---

### Post by markiep on 2008-01-19
I am in the same boat.  I am going to look around but i don't think we will find anything soon. :(

---

### Post by malibu on 2008-01-19
Yeah gotta love Microsoft.. Making something new and proprietary instead of using something tried and tested.

Yeah I never found anything.  Yesterday I set up a VM with WinXP on my Ubuntu and shut off every running service that I could.  I mapped all the drives that I need to get my media from, so it still exists on ubuntu.  I then backed up the VM image so I can just copy it back if it ever gets trashed.

IT's not quite working yet; I have a service shut off that I need to share.  The VM can detect my frame but not the other way around.

On the VM I'm also running 3GP Converter, which I like for my iPod vids and also I fell in love with Mediamonkey for my music organization.. Neither work with wine.

Anyway, I'll tell you how it goes!

---

### Post by mredub on 2008-01-19
I've got it working...

I had to go to the kodak website and update the firmware on my ex-811..  BUT!
if you install a uPNP media server like mediatomb or mythtv, you can run slideshows from this frame.

[http://mediatomb.cc/](http://mediatomb.cc/)

read up on how to add it to your software sources, and the you can add it from the synaptic package manager.  there wasn't a "version" for gusty listed yet..  but i got the fiesty one to work in gutsy just fine.

see this thread for more information on that:

[http://ubuntuforums.org/showthread.php?t=599980](http://ubuntuforums.org/showthread.php?t=599980)

Good Luck.. 

-Eric

---

### Post by malibu on 2008-01-20
Awesome.. That's good to know.

Not that it's necessary now, but this took me forever to figure out... To get this working via WinXP and sharing folders through Samba you must actually alter the registry.  The instructions can be found here:

[http://mechapixel.com/forums/showthread.php?t=221689](http://mechapixel.com/forums/showthread.php?t=221689)

---

