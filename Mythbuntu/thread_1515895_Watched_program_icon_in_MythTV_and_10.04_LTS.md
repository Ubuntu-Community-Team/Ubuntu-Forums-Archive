---
title: "Watched program icon in MythTV and 10.04 LTS"
date: 2010-06-23
forum: Mythbuntu
---

### Post by R3M3 on 2010-06-23
I just upgraded my box to 10.04 LTS (Lucid Lynx).

When I open the MythTV frontend, and go to the "Watch Recordings" screen there is no longer any indication (e.g. icon) of which shows are watched and which are unwatched. It doesn't seem to be an issue with MythTV not remembering the watched/unwatched status, as the popup menu changes from "Mark as Watched" to "Mark as Unwatched" as appropriate.

Is this a new "feature" of the latest MythTV, or is there something wrong with my system? I noticed that there was a "database needs to be updated to a new format" warning message when I first started - I'm concerned that the update might have been botched.

Thanks.

---

### Post by ian dobson on 2010-06-23
Hi,

Maybe clear out your thema cache (/home/MYTHTV-USER/.mythtv/thema or something like that).

I had to delete my cache/restart the frontend after upgrading to 10.04 as the graphics were totally screwed up.

Regards
Ian Dobson

---

### Post by R3M3 on 2010-06-23
I deleted the theme cache at ~/.mythtv/themecache, and that did not seem to change anything.

It seems that the issue is only in the "Mythcenter" theme. I tried the other themes, and they seem to have some sort of variation of the watched program icon. Apparently someone messed with the Mythcenter theme and removed the watched program icon. Unfortunately, Mythcenter is the only non-widescreen theme that's listed (I also am not partial to the others that are available, even if I had a widescreen).

---

### Post by matt06 on 2010-06-23
What version of mythtv are you running?  I recently updated my 0.23-fixes machines and I'm seeing the same thing using the Mythcenter theme.

---

### Post by R3M3 on 2010-06-24
I'm running the default version for Lucid ... which appears to be 0.23-fixes.

matt06, could you clarify? Did you mean that you updated to 0.23-fixes, and the icons disappeared, or is it that you were already running 0.23-fixes, updated something (e.g. Karmic to Lucid), and the icons disappeared. (I'm trying to puzzle out if it's a Lucid-specific issue, or if it's a general MythTV 0.23 issue.)

---

### Post by nickrout on 2010-06-24
The default version for lucid is NOT 0.23 fixes, no matter what ubuntu tells you. It is a rc2 version.

To get all the latest fixes (and a real 0.23-fixes) try installing the autobuilds package.

[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by matt06 on 2010-06-24
I am running Mythbuntu 9.10 with the autobuilds.  Previously I had 0.22 selected in the autobuilds section in MCC which was 23xxx-something?  I changed to 0.23 in MCC and now run 25xxx on both my FE and BE.  Using Mythcenter theme it used to show the "eye" next to episode title when "mark as watched" was set.  Since I've updated, the "eye" icon is non-existant regardless of the watched state.

Sorry I can't be more specific on the build number, my machines are down right now.

---

### Post by nickrout on 2010-06-24
sounds like a themeing issue everyone. Post to the themeing mailing list.

---

### Post by R3M3 on 2010-06-25
Did some digging and figured out the reason for the missing icon. Apparently the MythCenter theme under Karmic (MythTV 0.22?) used the default recordings-ui.xml, whereas there is a new MythCenter-specific recordings-ui.xml file under Lucid (MythTV 0.23?). 

Until (if?) they fix it, you can manually add the watched block from /usr/share/mythtv/themes/default/recordings-ui.xml to /usr/share/mythtv/themes/MythCenter/recordings-ui.xml
```

                            <statetype name="watched">
	                        <state name="yes">
	                            <imagetype name="yes">
	                                <position>5,5</position>
                                           <filename>small_watched.png</filename>
                                    </imagetype>
	                        </state>
	                        <state name="no" />
	                    </statetype>

```

(It goes after the "starttime" block and before the "playlist" block, though I'm not sure if the order/indentation will have any effect on MythTV.)

It's not perfect, as the icon overlaps with the text somewhat, but not enough to be an annoyance.

---

### Post by matt06 on 2010-06-26
Your fix worked good for me R3M3, thanks.

---

