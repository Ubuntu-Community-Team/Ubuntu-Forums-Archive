---
title: "[SOLVED] Edit Themes"
date: 2008-08-31
forum: Mythbuntu
---

### Post by uncle hammy on 2008-08-31
I know that all the themes are set with xml files, and I know those xml files reside in /usr/share/mythtv/themes/theme_name.  I even suspect that the file I need to edit is ui.xml.

What I am trying to do is edit my theme in Media Library>Watch Records list.  I am using the neo-wide theme, and currently, there is a bar around the selected item in both the Program Groups and Program Lists panes. The selected item in the active pane has a white font, and selected item in the inactive pane has a greyish font.  The distinction is not very clear on my screen, and I want to change the font of the actively selected item to red or something.  However, I seem to be having difficulty locating the correct xml file, and section of said file to edit to make this happen, or if I have found it, the changes don't seem to have any effect.

I found this section in ui.xml and changed "color" to red to test, with no effect....

```

<!--Watch Recordings-->
...
<window name="programfind">

    <font name="active" face="Bitstream Vera Sans">
      <color>#ffffff</color>
      <size>18</size>
      <size:small>14</size:small>
      <bold>yes</bold>
    </font>
...
</window>

```

Can anyone give me a hand with this please?

Thanks,
Scott

---

### Post by uncle hammy on 2008-08-31
Well, I found it!  I just needed to drop down one more window to "playback".  I looked at that section, but it just didn't seem right to me.

---

