---
title: "[SOLVED] Mythweb .htacces config"
date: 2008-02-25
forum: Mythbuntu
---

### Post by Calash on 2008-02-25
I am currently running MythTV 0.21

I have a Windows Mobile phone, and using the latest version of MythWeb you can now create .M3U play lists that link to a streaming file.  The woks great to play the streams on my phone, unless I enable the authentication.  From what I can tell there is no easy way to get a WM media player to authenticate so I can access the music.

The only way I can think to get this to work is to allow access to the streaming file while requiring authentication for the rest of MythWeb, however this is a bit beyond my current understanding of how to configure a .htaccess file.

Can anybody give me some pointers, or has anybody tried this yet?

Thanks

---

### Post by uopjohnson on 2008-02-25
I don't know anything about how the streaming file is setup.  Are they all in a single directory?  Or do they have a certain file name or extension that is unique?  If you can give me some details I can help with the .htaccess.  The basic premise will be to exclude authentication for files that meet a certain requirement (by name, or location).

---

### Post by Calash on 2008-02-25
Here is a copy of one line from the playlist, without the server name

> 
*********/mythweb/music/stream?i=1389#EXTINF:190,Metallica - Crash Course In Brain Surgery


I believe the /music is a redirect and not actually a folder, but I can not check that until I get home.  Each line is the same except for the i= variable...I assume that is called the song number.

I can get more info when I get home and can look at the file structure.

---

### Post by uopjohnson on 2008-02-25
I just recalled that you can send the http authentication credentials within a url.  So maybe you could modify whatever you are doing to point to 
https://user:yourpass@example.com/music/stream?i=blahblah

Since everything is pointed at the stream file this might also work:
 <Location /music/stream>
# All access controls and authentication are disabled
# in this directory
Satisfy Any
Allow from all
</Location>
The location directive is URL based so as long as you gave me the full path to the file it will work.  basically you want everything aver your server address.

---

### Post by Calash on 2008-02-25
I tried passed the credentials in the URL with no luck, came back not finding the server.  I will give the location a try and see what happens.


Thanks :)

---

### Post by Calash on 2008-02-26
On a related note, does anybody have a copy of the original .htaccess file for 0.21.  Been searching the web and cannot find a full copy.  Something is wrong with my current one, whenever I have authentication it only shows the site in handheld mode, so I cannot do any more testing.

I tried reinstalling Mythweb.....got nothing :(

Thanks

---

### Post by ravenp on 2008-03-13
Calash,

Perhaps you're having the same problem I was having. I recently upgraded to Mythtv/web 0.21. Mythweb was working fine from my PC browser until after I logged into Mythweb from my PDA using the same user. From then on, it only wanted to display the handheld/wap version of Mythweb in the browser on my PC, as long as I logged in as the same user.

I think it records the display settings for the current user in the database. Here's a note which tells you how to delete the settings for a user:

[http://www.mythtv.org/wiki/index.php/MythWeb#Mythweb_fails_to_detect_wap.2Fwml_devices_when_secured](http://www.mythtv.org/wiki/index.php/MythWeb#Mythweb_fails_to_detect_wap.2Fwml_devices_when_secured)

This 'worked' for me - although I lost my saved settings for the user. The recommendation is to create a different user for accessing from a PDA/handheld.

---

### Post by Calash on 2008-03-13
That makes sence.  I will give it a try and see how it works.  Thanks

I have to do a purge and reinstall of Mythweb first though....I really messed up the .htaccess.

---

