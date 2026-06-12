---
title: "How to get VLC to Autoplay CDs and DVDs"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by c0met on 2008-01-04
I have searched the forums and I have not found a version of the below method of setting autoplay in **VLC Media Player**, For this reason, I thought I'd make this post to explain how I got VLC to autoplay for me in case the knowledge is useful to someone else.

**FIRST**
You need to know the device identity and the command that VLC will use to open a CD or DVD.

**_[COLOR="DarkRed"]GETTING THE DVD COMMAND[/COLOR]_**
[LIST]
[*]start [COLOR="Purple"]**VLC Media Player**[/COLOR]
[*]click on [COLOR="Purple"]**Open File**[/COLOR]
[*]click on the [COLOR="Purple"]**Disc**[/COLOR] tab
[*]click on [COLOR="Purple"]**DVD**[/COLOR] radio button
[*]look down in the [COLOR="Purple"]**Customize**[/COLOR] text box and you'll see a command string. For me, the command was [COLOR="DarkRed"]**dvdsimple:///dev/scd0**[/COLOR]
[*]copy this command to (say) a blank open text document for easy, later retrieval
[/LIST]
**_[COLOR="DarkRed"]GETTING THE CD COMMAND[/COLOR]_**
[LIST]
[*]while VLC is open, click on the [COLOR="Purple"]**CD**[/COLOR] radio button
[*]copy and paste the [COLOR="Purple"]**Customize**[/COLOR] command string into the open text document. For me, the string was **[COLOR="DarkRed"]cdda:///dev/scd0[/COLOR]**
[*]close VLC
[/LIST]
**SECOND**
[LIST]
[*]Go to [COLOR="DarkRed"]**System >> Preferences >> Removable Drives and Media**[/COLOR]
[*]click on the **[COLOR="Purple"]Multimedia[/COLOR]** tab
[*]type [COLOR="Purple"]**vlc**[/COLOR] into the [COLOR="Purple"]**Command**[/COLOR] text box for[COLOR="Purple"]** Audio CD Discs**[/COLOR] and also for [COLOR="Purple"]**Video DVD Discs**[/COLOR]
[*]copy and paste the strings that you obtained from the VLC "Open" dialogue box into their appropriate command box (Note, make sure that there is a space between "vlc" and the command string.)
[/LIST]
After doing my [COLOR="Purple"]**Audio CD Discs, Command**[/COLOR], the text box contained,
[COLOR="DarkRed"]**[INDENT]vlc cdda:///dev/scd0[/INDENT]**[/COLOR]
And my [COLOR="Purple"]**Video DVD, Command**[/COLOR] text box contained,
[INDENT][COLOR="DarkRed"]**vlc dvdsimple:///dev/scd0**[/COLOR][/INDENT]

The process is now complete and you can close the **[COLOR="Purple"]Removable Drives and Media[/COLOR]** menu.

Regards,
c0met

---

### Post by DaveFP on 2008-01-15
Excellent little how-to, worked perfectly. Thanks!

---

