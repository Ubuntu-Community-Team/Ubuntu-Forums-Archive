---
title: "Possible to start program from MythTV gui?"
date: 2008-02-28
forum: Mythbuntu
---

### Post by fbn on 2008-02-28
Hi,

is it possible to start a program (like a mail reader or a game or a downloader) from the MythTV gui without logout and login with a different user?

Example: I'm in the MythTV gui watching a movie. Then I want to pause it, check my mails and switch back to the movie.

Thanks,
  Frank

---

### Post by axelsvag on 2008-02-28
Maybe it is to easy but if you start for example a program in the xubuntu/mythbuntu desktop environment first. And the start the frontend you just can use the alt+tab command to get access to your program.

---

### Post by franck3d on 2008-02-28
If you have a keyboard handy you could:
CTRL + ALT + Right Arrow to move to the second desktop, do your thing
then CTRL + ALT + Left Arrow to get back to myth.

---

### Post by Caps18 on 2008-02-28
I'm wondering about this too.  I'm sure it is possible since MythTV starts mplayer, but I would like to add a menu item that would start Google Earth in full screen mode.

---

### Post by ian dobson on 2008-02-28
Hi,

You could edit the xml menu file and add an extra button.

Try:-

cd /usr/share/mythtv
nano mainmenu.xml
then add something like:-

   <button>
      <type>Google</type>
      <text>Google maps</text>
      <action>EXEC /usr/bin/googlemaps</action>
   </button>

You might need to edit a different xml file. The actual file you must edit depends on which theme your using.

Regards
Ian Dobson

---

### Post by fbn on 2008-02-29
That sounds good - thanks!

---

### Post by laga on 2008-02-29
I think you can also copy the xml file to ~/.mythtv/. Otherwise, it'll be overwritten if there's a MythTV update. (dpkg-divert might work as well for that..)

---

