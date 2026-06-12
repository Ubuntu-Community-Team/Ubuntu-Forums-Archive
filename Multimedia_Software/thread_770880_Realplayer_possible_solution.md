---
title: "Realplayer possible solution"
date: 2008-04-27
forum: Multimedia Software
---

### Post by Fenris_rising on 2008-04-27
hi all
managed to install 8.04 today and have been tinkering ever since.
it seems many people are having trouble with real player. see this link for a guide from the BBC. follow the bit about repositories. basically you add a debian source to your source list. this contains real play. initially totem kept popping up to act as the player for the streamed audio listen again files 'RAM' what i managed to do was in the download window that shows the RAM file i opened its containing folder found the RAM file and right clicked it. click 'open with other application' in the window that pops up scroll down the list to find realplay highlight and open. worked like a charm. if it doesnt show in the list click the 'use a custom command' and navigate to the USR folder then BIN. real player is in here highlight and open. hope this helps some of you out. 
the link;
[http://www.bbc.co.uk/radio/help/faq/linux_and_unix_compatibility.shtml](http://www.bbc.co.uk/radio/help/faq/linux_and_unix_compatibility.shtml)

further to this i found i was having to do this everytime so i did a bit of digging in fire fox and heres what seems to have nailed it as the default action. open firefox then go to edit/preferences. select applications then look for the RA file under content type then look at what app is set to play it. if its not 'realplay' then click the dropdown arrow and click 'use other'
navigate to usr/bin as before and select realplay. seems to work for me. let me know how you all do. BTW im a novice so i have know idea what to do if this doesnt work for you. this works for listen again but im having bother with the bbc iplayer now lolol so so far stuff on radio 7. now i finf if when the iplayer opens you can click the 'listen using stand alone player' this means realplay gets used. ill keep faffing around and see if i can sort the rest out.

regards fenris

---

### Post by anrom on 2008-04-28
@Fenris_rising, you said: select applications then look for the RA file under content type then look at what app is set to play it. if its not 'realplay' then click the dropdown arrow and click 'use other'

What do you mean by the RA file?  I don't see anything by this name under content type.  I just had 8.04 installed the other day as well.  Thanks so much.

Edited to add that before my upgrade to 8.04 from Dapper, then Gutsy, I had a few BBC radio shows stored as Favourites in RealPlayer 11.0.  and I would play them from there rather than go to the website.  They still work now, but I can no longer get any other radio shows to play in standalone at the BBC site.  When I click on Play for a show, I get loud crackling sounds from the iPlayer.  Any help would be greatly appreciated.

---

### Post by Fenris_rising on 2008-04-29
hi there

maybe ive been lucky? i still cant use iplayer on mine i have to select use stand alone player. odd thing is i've just dual booted my laptop with kubuntu fiesty fawn installed realplayer as before and the iplayer works on it. heres a screen shot of my firefox preferences. ive just used gimp for the first time so i hope it works!!!!
under 'tools' 'plugins' realplayer plugin is on does that make any difference?? im 4 days old at linux so my help is limited.

---

### Post by anrom on 2008-04-29
@Fenris_rising, thanks for replying.  Since I've upgraded to Hardy Heron, I no longer see the "use standalone player" choice at the BBC iPlayer Radio browser.  I prefer storing shows in Favourites in  RealPlayer, now Helix Player in 8.04, since it saves the time of having to go to the website.  If I could find the location of each show, which starts with "rtsp://", I could add them back into my player.  I'm searching for the URLs for each show.

Previous to 8.04, I could just left-click on the iPlayer and it would open in realplayer.

Your gimp image is fine.  I don't have the realplayer plugin listed.  argh, this is the part of upgrades I hate.  anyone have any ideas on this?  much appreciated.

---

