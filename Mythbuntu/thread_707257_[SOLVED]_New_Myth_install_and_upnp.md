---
title: "[SOLVED] New Myth install and upnp"
date: 2008-02-25
forum: Mythbuntu
---

### Post by rickyble on 2008-02-25
I have been working on the myth install now for several weeks and think I have most hardware problems resolved and permanent fixes in place for them.  My immediate goals are to play mpgs and dvds copied to the mythtv thru a myth frontend attach to a tv. Long term capture HD OTA and capture satellite output from either svideo or component.   I tried Mediatomb to start with just to make sure I could see the upnp broadcast and could share and download to the media server machine and the hardware would work with 7 ubuntu.  Here is my setup and here is where I am.

Compaq sp700 dual 550s 1gig ram
30 hd / and /boot
250 gig hd /home
myth recordings redirected to /home/myth/recordings
Samba sharing /home/recordings/*
1 dtv tivo SD and 1dtv HD hacked to nonencrypted and on networked
 with both tysuite and tytoos installed

I have a tool that sniffs the network for upnp broadcasts which with Media tomb i could see.  I dont see the broadcast for the Upnp for mythbuntu.  Is there anything I need to configure or add?

Secondly I the website comes up ok but i get the following error for channel listings:

*Fatal Error* at /usr/share/mythtv/mythweb/includes/channels.php, line 58:
No channels were detected. Are you sure that MythTV is properly configured?

If you choose to *_submit a bug report 
<https://svn.mythtv.org/trac/newticket>_*, please make sure to include a
brief description of what you were doing, along with the following
backtrace as an attachment (please don't paste the whole thing into
the ticket).

------------------------------------------------------------------------
*Backtrace*:

    datetime:  2008-02-25 05:26:00 (EST)
    errornum:  256
  error type:  User Error
error string:  No channels were detected.  Are you sure that MythTV is properly configured?
    filename:  /usr/share/mythtv/mythweb/includes/channels.php
  error line:  58
  

I wish to download and convert my mpgs from dtv tivo and load them to the shared/recording directory of mythtv and then be able to play on the frontend hopefully a diskless frontend.  I have the download convert and copy to shares down and working.  I use the tysuite and it pulls them down from the tivo and encodes them on the fly and saves them to the mythbuntu share.  I dont see the saved recordings using the web piece.  Shouldnt they be there or am I again missing something?

Thanks in advance for any help

---

### Post by rddone on 2008-02-25
I dont know anything about the uPNP in myth, but perhaps I can shed some light on why the files in the recorded directory arent showing up.

This was probably a typo? Probably really the same directory?
[COLOR="RoyalBlue"]myth recordings redirected to /home/myth/recordings
Samba sharing /home/recordings/*[/COLOR]

I put all my mpg files in the directory for videos which defaults to /var/lib/mythtv/videos. There is a setting in myth that allows you to see files that arent in the db. Something like 'allow browse files'. Otherwise you have to go to setup/video manager to update the db to show the new files when you copy them to the videos directory.

I am not aware of a setting that allows you view the files in the recorded directory. It only shows files that are in the db. 

For me, it was much easier to put miscellaneous video files into the videos directory. 

HTH
Rob

---

### Post by rickyble on 2008-02-25
Yea my bad typo.  myth recordings redirected to /home/recordings

Thanks for the setting thats exactly what Im looking for.  You know where that setting is "for allow browse files'  Myth setup from the console or in the web piece?

---

### Post by newlinux on 2008-02-25
There used to be a packaging bug where you had to have the frontend installed on the master backend machine for UPnP to work. Don't know if it is still there, but I use UPnP and machines on my network are able to see the recordings...


I think that browse option is at:
Setup->Media Settings->Video Settings->General in mythfrontend.

But I'm not sure...

Also, I'm not sure I'm understanding exactly what you are trying to do. Are you trying to put shows that aren't recorded in myth in the recordings directory and expecting them to show up as myth recordings? I don't think that will work. You can put them in the mythvideo directory and scan them in or use the browse feature detailed above.

---

### Post by rickyble on 2008-02-25
Does any one know of anyway to check if Upnp  is installed or to install it after the fact?

Yes that is exactly what I am trying to do.  I wanted to use the frontend piece to be able to watch all the shows I have recorded using the tivos and converted.  How do you scan then in?
btw thanks

---

### Post by newlinux on 2008-02-25
Hmm, I did some checking on the forums and the packaging bug was fixed so that shouldn't be an issue anymore... I think with a backend install upnp is installed by default. I don't know if the upnp server is quite standards compliant so it won't work with all clients. What client are you using?

You scan them in by starting video manager in the frontend setup. This will make them available via upnp. They can be available via the media library videos section without scanning them in using the "Browse mode" referred to above. You have to put them in your videos directory however, not your recordings directory. You can set your videos directory in the mythfrontend setup menu as well. 

If you want to see them in the recordings screen you have to add them to the database. You can do this using myth.rebuilddatabase.pl, but it is time consuming:

[http://www.mythtv.org/wiki/index.php/Frequently_Asked_Questions#How_do_I_import_recordings_from_other_sources_into_Myth.3F](http://www.mythtv.org/wiki/index.php/Frequently_Asked_Questions#How_do_I_import_recordings_from_other_sources_into_Myth.3F)
[http://www.myhdbox.com/mythtips/2006/05/tip-3-importing-downloaded-tv-shows.php](http://www.myhdbox.com/mythtips/2006/05/tip-3-importing-downloaded-tv-shows.php)

---

### Post by rickyble on 2008-02-25
Actually its a client brower network scanner from intel.  It sniffs the network for upnp broadcast.  I did see the mediatomb advertising but not anything using mythtv.

---

### Post by rickyble on 2008-02-26
Anyone got any ideas on the errors listed in the first about the channels not showing up when I open the browser to the website?

---

