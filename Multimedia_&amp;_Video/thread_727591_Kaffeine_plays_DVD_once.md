---
title: "Kaffeine plays DVD once"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by MonsterTrimble on 2008-03-17
Hey all;

My Kaffeine is acting odd and I assume it's something stupid. If I start up my machine and attempt to watch a DVD (.iso or physical disk) it will do it without hesitation. If I eject th media or try to switch to something else I get the error message "The Source can't be read. Maybe you don't have enough rights for this, or source doesn't contain data (e.g. no disc in drive). (/dev/dvd)" and then a second window pops up asking if I want to install the required codecs, which I do have installed because I was just watching another damn movie!

I have tried un and reinstalling Kaffeine, I have installed every codec known to man and beast, and read thru a lot of posts, both here and on other forums. The only thing I can see is a bug in Linux itself, but since this thing was working flawlessly for months (until k9copy was uninstalled recently due to KDE4 switchover) I think it's something else. 

Help!

---

### Post by kenny1948 on 2008-03-17
I had problems playing DVD's I am located in the USA, and it seems some of the players in Ubuntu are simply set to play PAL format. 

I downloaded klv player, you can get it with synaptic package manager. You have to have the xine codecs downloaded with it. It works fine with all my DVD's but I had to set it up as my default player. You can do that with <system<preferences<removable drives and media.  Then under the multimedia tab,  go to the middle box (video DV Discs ) and change whatever is there to vlc %m and you're in business. If for some reason it doesen't work simply go back and restore whatever player you had setup as default. Just change the name and keep % m

Likewise I discovered a file converter, that so far has worked perfect. If you like to burn DVD's and need to convert files this works great. 
It is winff and can be found at this website. You can download the file from this website [http://www.winff.org/index.php?option=com_content&view=category&layout=blog&id=34&Itemid=60]("http://www.winff.org/index.php?option=com_content&view=category&layout=blog&id=34&Itemid=60"), and it can then be installed with the installer built into Gutsy. It downloaded and installed very easily. I was surprised. The site has information explaining the program as well.:) If you should decide to install it, use the Debian package newest release.

---

### Post by acirilo on 2008-03-18
> **kenny1948 said:**
> I had problems playing DVD's I am located in the USA, and it seems some of the players in Ubuntu are simply set to play PAL format. 

I downloaded klv player, you can get it with synaptic package manager. You have to have the xine codecs downloaded with it. It works fine with all my DVD's but I had to set it up as my default player. You can do that with <system<preferences<removable drives and media.  Then under the multimedia tab,  go to the middle box (video DV Discs ) and change whatever is there to vlc %m and you're in business. If for some reason it doesen't work simply go back and restore whatever player you had setup as default. Just change the name and keep % m

Likewise I discovered a file converter, that so far has worked perfect. If you like to burn DVD's and need to convert files this works great. 
It is winff and can be found at this website. You can download the file from this website [http://www.winff.org/index.php?option=com_content&view=category&layout=blog&id=34&Itemid=60]("http://www.winff.org/index.php?option=com_content&view=category&layout=blog&id=34&Itemid=60"), and it can then be installed with the installer built into Gutsy. It downloaded and installed very easily. I was surprised. The site has information explaining the program as well.:) If you should decide to install it, use the Debian package newest release.
where is the klv player?

i can't seem to find it

---

### Post by mc4man on 2008-03-18
> t seems some of the players in Ubuntu are simply set to play PAL format. 
pc's and software players (unlike most standalones) are unaffected by format, i.e. pal vs.ntsc
Though _sometimes_  drive, media region mismatches can be an issue - pal usually being region 2, most ntsc' s region 1
winff looks interesting - curious how it does a pal>nstc conversion
@op - possibly issues with kaffeine due to kde4

---

