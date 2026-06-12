---
title: "Best Way to View YouTube within 9.10?"
date: 2009-12-01
forum: Mythbuntu
---

### Post by Singing Dwarf on 2009-12-01
I am looking for the best way to view YouTube videos within Mythbuntu 9.10.

I have searched these forums and there seem to be various options, including MythVodka and MythStream.

I have a fully working installation and dont want to mess it up trying the various options, when I'm not 100% sure any of them will work with 9.10.

Can anybody please confirm what they are using for accessing YouTube in an installation similar to above?

---

### Post by theophile on 2009-12-01
I assume you want to view YouTube in MythTV? You've listed the only options available. The other one is to create a menu item for Firefox which you can launch from MythTV.

---

### Post by Singing Dwarf on 2009-12-01
That's right, I want to view in MythTV.

I'm curious as to whether either of the options I listed are actually working in Mythbuntu 9.10 and if so, whats the best way of getting them to work!?

---

### Post by andy-roo on 2009-12-02
If those options don't work out you could try Boxee.  I have been using it for YouTube and some other things.  It is possible to start Boxee from within MythTV by creating your own menu entry.

Simply add the following to "~/.mythtv/mainmenu.xml"
> 
   <button>
     <text>Boxee</text>
     <action>EXEC /opt/boxee/Boxee</action>
   </button>

And make sure to place it in the order you want the buttons to appear.  For example I placed mine just after the "Media Library" button.

---

### Post by SiHa on 2009-12-02
+1 for Boxee.

It has the advantage over Firefox / Mythbrowser that it is optimized for TV and Remote, and the advantage over Mythstream and Mythvodka is that it actually works!

Boxee isn't officially available for Karmic yet (well it wasn't a few weeks ago), but I followed the instructions [[COLOR="Blue"]_here_[/COLOR]](http://forum.boxee.tv/showpost.php?p=67448&postcount=8) and it worked perfectly.

Note that you need to register for a Boxee account before you can use it, and you'll probably want to stop following Avner Ronen, particularly if you're not in the US.

---

### Post by andy-roo on 2009-12-02
Yeah, it saved me from quite a headache.  When I first installed Boxee I was overjoyed about how polished it is.

I almost forgot to mention to install Boxee you need to add the following to "/etc/apt/sources.list"
> deb [http://apt.boxee.tv](http://apt.boxee.tv) jaunty main

And run "sudo apt-get install boxee" for those with 9.04.  Except for those with 9.10 should use SiHa's instructions.

---

