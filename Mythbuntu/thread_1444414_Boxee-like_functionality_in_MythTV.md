---
title: "Boxee-like functionality in MythTV"
date: 2010-04-01
forum: Mythbuntu
---

### Post by kens8 on 2010-04-01
I'm building a Mythbuntu box, but I also watch a lot of web shows.  Is there a plugin for Boxee-like functionality to MythTV, or should I just switch between the two?

---

### Post by dibuntux on 2010-04-01
You can just add a button to launch Boxee from myth menu; this is what I did - just beware that the 64bit version run SLOW on Mythbuntu (it is ok on Ubuntu) - see the appropriate thread here...

This is what you have to do:

Boxee
(overwritten at any update...)

For anyone using Mythtv .22, adding a launcher to the menu is slightly different because of MythUI.

Additions to /usr/share/mythtv/themes/defaultmenu/mainmenu.xml
Code:

   <button>
     <type>MENU_BOXEE</type>
     <text>Boxee</text>
     <action>EXEC /opt/boxee/run-boxee-desktop</action>
   </button>

   <button>
     <type>MENU_XBMC</type>
     <text>XBMC</text>
     <action>EXEC /usr/bin/xbmc</action>
   </button>

If you have custom icons, additions to /usr/share/mythtv/themes/nameoftheme/menu-ui.xml | In my case, /usr/share/mythtv/theme/blootube-wide/menu-ui.xml

Code:

            <state name="MENU_BOXEE">
                <imagetype name="watermark">
                    <filename>watermark/boxee.png</filename>
                </imagetype>
            </state>

            <state name="MENU_XBMC">
                <imagetype name="watermark">
                    <filename>watermark/xbmc.png</filename>
                </imagetype>
            </state>

If this doesn't work for your particular theme, run mythfrontend.real from a terminal, check the paths of the window and menu themes loaded, and make the changes accordingly.

---

### Post by kens8 on 2010-04-01
Excellent!  Thank you!

---

