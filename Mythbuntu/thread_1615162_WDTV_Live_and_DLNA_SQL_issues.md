---
title: "WDTV Live and DLNA SQL issues"
date: 2010-11-06
forum: Mythbuntu
---

### Post by mnclayshooter on 2010-11-06
I've successfully built and am using a mythtv box based on 10.04.  
 
Recordings work like a charm, however, I have some playback issues using my WDTV-Live.  Recordings on certain channels will NOT play back using DLNA "Media Servers" however they'll play perfectly through Samba.  
 
That being said, I, using my exceptional detective skills to deduce that there's nothing wrong with the file nor with my WDTV-Live (at least not its functionality), and not with my network/router etc.
 
[COLOR=black]Well, after quite a bit of searching and tinkering... I've determined that this occurs due to the OTA broadcast not having the subtitle information in the EIT data.  Myth defaults to using the description as subtitle.  The description is usually a few sentences long which is why the DLNA is rejecting the connection - its way too long.  I can prove this time and time again by using the ubuntu add-on phpmyadmin and editing the 'recorded' data in the myth SQL file to be shorter.  The recordings play like a charm once the description is shortened. [/COLOR]
[COLOR=black] [/COLOR]
[COLOR=black]There's some posts online about editing upnpcdstv.cpp with the following data:[/COLOR]
[COLOR=black] [/COLOR]
[COLOR=black]line 276:
QString sName = sTitle + ": " + (sSubtitle.isEmpty() ? sDescription :
sSubtitle);
with this:
QString sName = sTitle + ": " + (sSubtitle.isEmpty() ? "" : sSubtitle);

[/COLOR]
[COLOR=black]But my very limited knowledge is that you'd have to recompile the entire myth backend in order to do this.  I haven't tried it, but given the results of editing the SQL info and having success using the WDTV LIve, I'd say this probably would work. [/COLOR]
[COLOR=black] [/COLOR]
[COLOR=black]Anyone else tried this?  Any pointers for a relatively inexperienced linux user? [/COLOR]

---

### Post by nickrout on 2010-11-17
The developers do not lurk here, you need to post this to trac with a proper patch file.

---

