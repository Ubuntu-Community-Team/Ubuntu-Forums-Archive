---
title: "Upgrading to 10.01"
date: 2011-01-30
forum: Mythbuntu
---

### Post by dvystrcil on 2011-01-30
Hi Folks,

Probably been asked a hundred times, but I am not getting any good search hits. I am interested in upgrading from 9.10 to 10.01 (the updater is really nagging me to do this) and would like to know if there are any "gotchas". This the family's primary source for TV/Music/DVD box. I would really hate to run the update and found I mess things up. 

Any advice would be appreciated.

Thanks,

--Dan

---

### Post by nickrout on 2011-01-30
I assume you mean 10.10 :)

But if it is working, why change?

---

### Post by dvystrcil on 2011-01-31
Actualy its wanting me to upgrade to 10.04.1 ;)

Two reasons to upgrade (though they aren't strong ones):

1) I can start using .25
2) I will be using a LTS version.

---

### Post by myth1914 on 2011-01-31
I recently went through the upgrade from 10.04 to 10.10.  I believe you'll have to go LTS 10.04 first for the full update; however, in my experience...

Benefits (of 10.10): ALSA update, supporting HDMI audio through my video card.  Myth update (haven't explored this to provide detail though)

Gotchas 10.04 and 10.10: PHP5 errors, although I suspect I wouldnt have near the issue if I would have let the upgrade install the new PHP.ini  This was most apparent with PHPMyAdmin and zoneminder

10.04 required a patch for VMware server.  I had to move to player with 10.10 as support is dropping off with the end of life.  Don't know if you use it, but Player requires the screen rather than powered in the background, although this is new to me and i'll probably port over to virtualbox.

Either way, if you're running myth, you'll have to update all FEs due to the schema change.  Hope that helps.

---

