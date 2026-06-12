---
title: "Add menu items in 9.10 mythbuntu theme"
date: 2009-11-25
forum: Mythbuntu
---

### Post by newbie02 on 2009-11-25
All,
Since installing 9.10 I can not figure out what xml file i need
to edit. Im using Mythbuntu theme.
I have been looking in here /usr/share/mythtv/
But am not sure. I am trying to add a button under Media Library->Boxee.

Thanks for the help.
Newbie02

---

### Post by uncle hammy on 2009-11-25
/usr/share/mythtv/themes/defaultmenu

the 2 that I modify are mainmenu.xml and library.xml (which will put items under Media Library)

Keep a backup if files after you modify them, because every update will over write them.

---

### Post by Neon Dusk on 2009-11-25
If you copy the xml file you want to edit to ~/.mythtv/ then make the changes there it won't be overwritten when myth is updated.

---

### Post by uncle hammy on 2009-11-25
Copy to where in ~/.mythtv?

---

### Post by newbie02 on 2009-11-25
That was it. 
Thanks everyone.
Newbie02:popcorn:

---

### Post by azmyth on 2009-11-25
> **uncle hammy said:**
> Copy to where in ~/.mythtv?

/home/username/.mythtv

where username is the FE user.

---

### Post by Neon Dusk on 2009-11-26
> **uncle hammy said:**
> Copy to where in ~/.mythtv?

If you want to modify 
/usr/share/mythtv/themes/defaultmenu/mainmenu.xml

copy it to

~/.mythtv/mainmenu.xml
or /home/frontendusername/.mythtv/mainmenu.xml (if you're not logged as the user that usually runs the frontend)

---

### Post by molder on 2010-03-04
Is it possible to add icons?  My Hulu Desktop looks so naked with no icon.

---

### Post by dibuntux on 2010-03-04
Yes it kept overwriting... so, I copy it to

~/.mythtv/mainmenu.xml

And it is ok. I also found that menu-ui.xml is in the home directory; I tried to modify it for adding an icon to the main menu:

<state name="MENU_BOXEE">
                <imagetype name="watermark">
                    <filename>watermark/boxee.png</filename>
                </imagetype>
            </state>

but it does not work: only works with file in 
/usr/share/mythtv/themes/nameoftheme/menu-ui.xml

Any ideas? TIA

---

### Post by xinix on 2010-03-04
> **dibuntux said:**
> Yes it kept overwriting... so, I copy it to

~/.mythtv/mainmenu.xml

And it is ok. I also found that menu-ui.xml is in the home directory; I tried to modify it for adding an icon to the main menu:

<state name="MENU_BOXEE">
                <imagetype name="watermark">
                    <filename>watermark/boxee.png</filename>
                </imagetype>
            </state>

but it does not work: only works with file in 
/usr/share/mythtv/themes/nameoftheme/menu-ui.xml

Any ideas? TIA

Try giving it the absolute location of the watermark file.

---

### Post by molder on 2010-03-04
So if I where to add ```
<state name="Hulu">
<imagetype name="watermark">
<filename>/home/andrew/.mythtv/themes/hulu.png
</filename>
</imagetype>
</state>
``` in menu-ui.xml?

menu-ui.xml

```
<mythuitheme>
    <window name="mainmenu">
        <font name="menufont" from="basesmall">
            <color>#666666</color>
        </font>
        
        <imagetype name="background" draworder="0">
            <area>0,0,1280,720</area>
            <filename>images/backgrounds/</filename>
        </imagetype>
        
        <imagetype name="menuscrollback">
            <area>-8,580,1296,30</area>
            <filename>images/menuscrollback.png</filename>
            <alpha>200</alpha>
            </imagetype>
          
        <buttonlist name="menu">
        
            <area>0,559,1280,60</area>
            <layout>horizontal</layout>
            <spacing>20</spacing>
            <scrollstyle>center</scrollstyle>
            <wrapstyle>items</wrapstyle>
            <buttonarea>0,0,1280,60</buttonarea>
            <statetype name="buttonitem">
                <state name="active">
<!--                    <area>0,9,240,59</area>-->
                    <area>0,9,413,59</area>
                    <imagetype name="background" />
                    <textarea name="buttontext">
<!--                        <area>0,0,240,59</area>-->
                        <area>0,0,413,59</area>
                        <font>menufont</font>
                        <align>center,vcenter</align>
                        <cutdown>yes</cutdown>
                        <case>upper</case>
                    </textarea>
                </state>
                <state name="selected"> 
<!--                    <area>0,9,240,59</area>-->
                    <area>0,9,413,59</area>
                    <imagetype name="background" />
                    <textarea name="buttontext">
<!--                        <area>-17,0,274,59</area>-->
                        <area>-17,0,447,59</area>
                        <font>basesmall</font>
                        <alphapulse min="180" max="255" change="2"/>
                        <align>center,vcenter</align>
                        <cutdown>yes</cutdown>
                        <case>upper</case>
                    </textarea>
                </state>
                        
        </buttonlist>
        
        <imagetype name="clockback">
            <area>525,695,230,51</area>
            <filename>images/clock_backdrop.png</filename>
        </imagetype>
        
        <clock name="clock">
            <area>529,700,219,25</area>
            <font>clock</font>
            <format>%DATE%, %TIME%</format>
            <align>center</align>
            <alpha>255</alpha>
        </clock>
        
        <imagetype name="clockbackoverlay">
            <area>525,695,230,23</area>
            <filename>images/clock_backdrop_overlay.png</filename>
        </imagetype>
        </buttonlist>
        
    </window>
</mythuitheme>

```

---

### Post by dibuntux on 2010-03-05
No, giving it the absolute location of the watermark file does not work. I tried and it does not load the logo. My boxee logo is in the watermark dir.
But then again: why should the absolute location path work when the path is relative to just /watermark for the other buttons (that work) in the same directory?

Because the file menu-ui.xml in home is not the one that is beeing read. It works for mainmenu.xml but not for menu-ui.xml
 Any other ideas? TIA

---

### Post by smontclair on 2010-03-23
> **uncle hammy said:**
> /usr/share/mythtv/themes/defaultmenu

the 2 that I modify are mainmenu.xml and library.xml (which will put items under Media Library)

perhaps I'm missing something obvious, but the mainmenu.xml here doesn't correspond to the highest level menu on my frontend. 

the menu items there are TV, Music, Videos, Images, Weather, Archive Files, Movie Times, Setup.

where is the xml file for this menu? or is there a way to force it to use the mainmenu.xml file? 

THANKS!

---

### Post by nickrout on 2010-03-23
> **dibuntux said:**
> No, giving it the absolute location of the watermark file does not work. I tried and it does not load the logo. My boxee logo is in the watermark dir.
But then again: why should the absolute location path work when the path is relative to just /watermark for the other buttons (that work) in the same directory?

Because the file menu-ui.xml in home is not the one that is beeing read. It works for mainmenu.xml but not for menu-ui.xml
 Any other ideas? TIA

file permissions?
wrong file format? (I don't know if myth expects a certain size, depth, format etc for watermarks)

---

