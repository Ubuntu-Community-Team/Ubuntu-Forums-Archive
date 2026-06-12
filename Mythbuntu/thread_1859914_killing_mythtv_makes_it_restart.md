---
title: "killing mythtv makes it restart"
date: 2011-10-14
forum: Mythbuntu
---

### Post by My Name on 2011-10-14
hi, i've been away from these forums for a while as all has been well, but i now have one little irk.
I have set my system up to use mythtv for live tv and recordings, but with xbmc for video and music. i have used a script that kills myth and starts xbmc and vice versa using a rc keypress. the problem is it seems that any programme that is killed in this way is forced to restart. is there any way of stopping this.

I am using this scrypt if it helps.
[http://www.technazgul.com/2011/03/switching-between-xbmc-and-mythtv-via.html?showComment=1318516355909#c4942580235150284877]("http://www.technazgul.com/2011/03/switching-between-xbmc-and-mythtv-via.html?showComment=1318516355909#c4942580235150284877")

---

### Post by thatguruguy on 2011-10-14
Just out of curiosity, why kill the mythtv frontend when you run xbmc?

I have XBMC as a menu item on my mythfrontend, and run it directly from there.  There are no LIRC conflicts or any other problems when doing so.

---

### Post by shad0w_walker on 2011-10-14
I'll second that suggestion. If you want to run another program, just add it to a mythtv menu. The menus are just defined as .xml files and you can edit them to completely customise them. The option you would want is the 'exec' command, while it's running another program, mythtv (Frontend) won't do anything until that program exits. Seems the best option unless you really need to free up ram?

---

### Post by superm1 on 2011-10-14
Thirded.

Here's exactly how to do that:

[http://tips.myhdbox.com/2006/04/tip-2-how-to-customize-mythtvs-menus.php](http://tips.myhdbox.com/2006/04/tip-2-how-to-customize-mythtvs-menus.php)

---

### Post by My Name on 2011-10-15
yeah i've done that actually but I wanted to use a jump point assigned to the dvd button on the remote. if you could tell me how to create a new jump point, or manipulate the current DVD jump point to open xbmc instead of mythtv's movie menu, that would be even better.
Is the kill then restart thing new? i haven't noticed it before. it's probably quite good for most situations but i guess it can be a bit of a pain for others. is there a way of disabling it? it may be useful to know in the future if not for this situation.

---

### Post by shad0w_walker on 2011-10-15
You should be able to edit the dvd menu XML and replace the call to open the DVD play with the 'exec' command you need.

---

### Post by My Name on 2011-10-15
...also is it possible to switch between the two via a button press? i'm thinking i could have them both start from boot and then use the remote to switch between the two. it would mean a more seamless integration. maybe the menu entry could do the same...

---

### Post by My Name on 2011-10-15
> **shad0w_walker said:**
> You should be able to edit the dvd menu XML and replace the call to open the DVD play with the 'exec' command you need.

do you know where i can find that xml? and would i just need to replace the command with 'exec xbmc'? i'm not too hot on the commands...

---

### Post by shad0w_walker on 2011-10-15
I don't know about having both running and switching, never tried that and don't know that much about xmbc. The files you need are in /usr/share/mythtv/ If you copy the files you want to edit to .mythtv in the home folder of the user running the front end it will override the defaults so you always have a backup if you make a mistake. The file you're looking for should be videomenu.xml. The bit you want to edit looks like this:
```

<button>
  <type>DVD_PLAY</type>
  <text>Play DVD</text>
  <action>DVD_PLAY</action>
</button>

```

If you change <action>DVD_PLAY</action> to <action>exec xmbc</action> it should work. If xmbc isn't the command you run to launch xmbc, just put in whatever you need :P

---

### Post by My Name on 2011-10-15
> **shad0w_walker said:**
> I don't know about having both running and switching, never tried that and don't know that much about xmbc. The files you need are in /usr/share/mythtv/ If you copy the files you want to edit to .mythtv in the home folder of the user running the front end it will override the defaults so you always have a backup if you make a mistake. The file you're looking for should be videomenu.xml. The bit you want to edit looks like this:
```

<button>
  <type>DVD_PLAY</type>
  <text>Play DVD</text>
  <action>DVD_PLAY</action>
</button>

```

If you change <action>DVD_PLAY</action> to <action>exec xmbc</action> it should work. If xmbc isn't the command you run to launch xmbc, just put in whatever you need :P
that's not doing it i'm afraid. I need to find the xml that contains ```
 <button>
     <type>JUMP_VIDEO_GALLERY</type>
     <text>Videos</text>
     <action>JUMP Video Gallery</action>
     <depends>mythvideo</depends>
   </button>
```
i think this is what affects the jump points
i have no idea where it is and i can't find the info i need...

---

