---
title: "Driver Not Cutting It"
date: 2011-07-15
forum: Multimedia Software
---

### Post by zorph on 2011-07-15
So i installed the NVIDIA accelerated graphics driver using the 'additional drivers' program. And clearly it is working kinda because without it i cant eve open EVE Online game, and also the setting manager for NVIDIA is working. But when i install it i can go as far as the character walking around station(with awful pixel rendering)...then it freezes cuz graphics is so bad. The driver says its activated, but currently not in use. I know that my graphics card could perform better than this...it is a: Galaxy Geforce GT 430 Fermi 1GB Memory DDR3 DirectX 11 128-bit ( [ [http://www.newegg.com/Product/Produc...82E16814162067](http://www.newegg.com/Product/Produc...82E16814162067) ) 

I am running with a MSI NF725GM-P31 AM3 NVIDIA GeForce 7025 & nForce 630a Micro ATX AMD Motherboard ( gpu is using PCI 16x2 slot )
2x2gb Kingston DDR3 RAM
530 Watt Raixmax PSU
3.2 ghz dual core AMD Athlon II CPU (not overclocked)
nothing is overclocked.

Running UBUNTU 11.04

Is there some other driver i can install that is more effective, and how do i install it?

---

### Post by mikewhatever on 2011-07-15
According to the system requirements ([http://support.eveonline.com/Pages/KB/Article.aspx?id=124](http://support.eveonline.com/Pages/KB/Article.aspx?id=124)), the game client is only available for Windows and MAC. How do you run that on Ubuntu?

---

### Post by zorph on 2011-07-15
I installed Wine and wine tricks... install vcrun2008 2005 idk which one i just did all of them. then i configure it for windows xp. u have to install a arial font and then change audio to oss instead of whatever it is defaut on wine config. then u have to create a launcher so it doesnt lock up and u cant close it. but right now it just freezes after about 2minutes so i have to force quit anyway :/

---

### Post by mikewhatever on 2011-07-15
Ah, I see. So you've installed the Windows client in Wine and have assumed that the driver doesn't cut it. I strongly suspect that the problem is elsewhere. Have you checked the AppDataBase to verify  that the client works well in Wine?
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by zorph on 2011-07-15
Yes i have checked the list and EVE has a Gold star rating. One thing tho is this:

Jukebox work perfect using the last mpg123 lib version (currently mpg123-1.13.2.tar.bz2 ) at  [http://sourceforge.net/projects/mpg123/](http://sourceforge.net/projects/mpg123/)  and later compile wine with the flag --with-mpg123 (if you make your own builds, Wine package already use it)

I copied that from the winehq but i dont know how to install this or like where to install it too, i know this is another thing i need to fix. the audio keeps looping when i log in.

So youre saying that the driver that comes prepackaged with "additional drivers" that says "NVIDIA accelerated graphics driver" is the latest and greatest i can get right now for my card and there is no way to improve driver?

---

### Post by mikewhatever on 2011-07-15
> **zorph said:**
> ...

So youre saying that the driver that comes prepackaged with "additional drivers" that says "NVIDIA accelerated graphics driver" is the latest and greatest i can get right now for my card and there is no way to improve driver?

No, I didn't say any of that. I am not convinced the driver is at all relevant to the problem, but if you feel adventurous and want to try the latest and greatest, by all means, do.
[http://www.phoronix.com/scan.php?page=news_item&px=OTYyMw](http://www.phoronix.com/scan.php?page=news_item&px=OTYyMw)

---

### Post by zorph on 2011-07-15
Thanks for the link. and i think your right cuz i can run the game 'tremulous' at 90fps... and with eve online at minimum settings it still looks wicked buggy and glitchy once i log in. however up to that part the log in and everything seems perfect. After about 50 seconds of walking around it freezes.

I dont understand how to install driver correctly. i can download things and use sudo apt-get, but idc how to compile source files. so maybe you could give me a link to a guide or tell me exactly how to install that new driver for my graphics card?

---

### Post by rickytikki on 2011-07-15
In my experience games on wine run with some lag. i just installed anno 1401 i have and icore5 with nvidia 8600gt and still i get lag and i had to use a no cd crack. In my experience its better to do a dual boot and use windows just for games thats what i do

---

### Post by RedeyeAce on 2011-07-15
Heya Zorph,

Ive been playing eve for about 5 years now, The incarna update with walking in stations is bugged to hell and back and they know it. Everyone is having major problems and If you can get it to run over 10fps your in a minority.

Just be thankful you aren't running an ATI card, cos some users with crossfire are having their cards fried.  Its that bad.

In windows VHP 64bit it uses all 4gb ram and a 1.3gb pagefile and with minimum settings I get a whopping 6 FPS

In Ubuntu it uses 1.3Gb ram 0 pagefile and runs at about 20FPS, got some visual tearing tho, which is has to be played with in the settings of eve and playing with nouveau ubuntu drivers, just haven't got round to it yet.

Basically, don't use walking in stations, thats what most of us do. Sit around :popcorn: and wait for CCP to get round to fixing it. Theyve got bigger problems on the horizon tho :)

Sorry its not a constructive this is how you fix it reply. Its not your setup or drivers, yes you can probably tw.eak it a bit better, but its Incarna and waiting for CCP to fix it

---

### Post by mikewhatever on 2011-07-16
> **zorph said:**
> ...

I dont understand how to install driver correctly. i can download things and use sudo apt-get, but idc how to compile source files. so maybe you could give me a link to a guide or tell me exactly how to install that new driver for my graphics card?

Unfortunately, there isn't a pretty way to manually install Nvidia drivers. Ubuntu automates the process with the Additional Drivers Utility, but you feel really really bored, here is your guide.
[https://help.ubuntu.com/community/NvidiaManual#Complete%20Manual%20Install](https://help.ubuntu.com/community/NvidiaManual#Complete%20Manual%20Install)

---

### Post by zorph on 2011-07-16
Ok now for some reason it is working better. I am getting20-30 fps in station and 60-100 fps out of station! In station it is a bit buggy but i think the gameplay once undocked is going great. 

Now my biggest trouble is that it crashes now and then for some reason and i have no idea how to fix that. but i think the driver is fine. so i will start a new thread maybe

---

### Post by RedeyeAce on 2011-07-16
Heya Zorph,

Try putting your queries up on the eve forums as well if you havent already, theres a linux section, im assuming you've read the eve linux wiki?

[http://www.eveonline.com/ingameboard.asp?a=channel&channelID=630463](http://www.eveonline.com/ingameboard.asp?a=channel&channelID=630463) 

Hope you get it sorted :)

---

### Post by zorph on 2011-07-16
Thanks for the tips and yeah i have been looking on eve linux forum but i havnt made a thread yet cuz it wouldnt let me for some reason. Like when i log in i cant see the new thread link anymore. But oh well. 

I have gotten eve working 60-100 fps out of station so im fairly happy. only prob now is it crashes now and then, but if i turn off the station environment that seems to help it not crash. Also in game browser causes game to freeze, but for now its good enough...

---

