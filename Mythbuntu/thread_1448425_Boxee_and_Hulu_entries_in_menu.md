---
title: "Boxee and Hulu entries in menu"
date: 2010-04-06
forum: Mythbuntu
---

### Post by williammanda on 2010-04-06
I'm trying to make entries for boxee and hulu in the mythtv menu. This is what I'm using:

/usr/share/mythtv/themes/defaultmenu/mainmenu.xml

<button>
<type>MENU_BOXEE</type>
<text>Boxee</text>
<action>EXEC /opt/boxee/run-boxee-desktop</action>
</button>

<button>
<type>TV_WATCH_RECORDINGS</type>
<text>Hulu</text>
<action>EXEC /usr/bin/huludesktop</action>
</button>

I inserted the entries after tv_watch_recordings but I don't see any entries when I start mythtv.

I'm using mythbuntu wide theme.

---

### Post by Lepy on 2010-04-06
A better approach is to make a copy of the mainmenu.xml and place it in /home/yourusername/.mythtv/mainmenu.xml

The mythtv frontend will read this new file on start. It is especially useful if you subscribe to fixes or trunk as each new update will overwrite /usr/share/mythtv/themes/defaultmenu/mainmenu.xml


Here are the entries I use:
```
   <button>
     <type>MENU_XBMC</type>
     <text>XBMC</text>
     <action>EXEC /usr/bin/xbmc</action>
   </button>

    <button>
        <type>MENU_HULU</type>
        <text>Hulu</text>
        <action>EXEC /usr/bin/huludesktop %F</action>
    </button>

   <button>
     <type>MENU_BOXEE</type>
     <text>Boxee</text>
     <action>EXEC /opt/boxee/run-boxee-desktop</action>
   </button>

```

It seems like your entries are formatted correctly. Just make sure they stay inside the </mythmenu> tags.

---

### Post by williammanda on 2010-04-06
OK I found the issue. I'm using classic. So I need to edit the mainmenu.xml for classic.

Lepy
Thanks for the insight, I will use your method.

---

