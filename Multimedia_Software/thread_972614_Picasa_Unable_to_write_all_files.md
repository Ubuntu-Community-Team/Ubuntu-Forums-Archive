---
title: "Picasa: Unable to write all files"
date: 2008-11-05
forum: Multimedia Software
---

### Post by windfix on 2008-11-05
I am using Intrepid and Picasa.  When I attempt to "export files to folder" from Picasa - for instance to reduce the resolution for web posting - I get:

"Unable to write all files due to a disk error.  Disk may be full or readonly."

My disk (home partition) has 50 GB free, and I have checked the permissions on the Picasa Exports folder (user = read, write; group = read, write; everyone = read)

Any clues?

To confound this, I attempted one group of photos and got this error repeatedly.  I rebooted, thinking something needed reset, and the next attempt worked!  Then when I tried another set of photos, back to the error.  Rebooting did nothing this time.

---

### Post by windfix on 2008-11-13
Anyone?  This issue is making me nuts.

---

### Post by Fir3chi3f on 2008-11-13
Im not to familiar with Pacasa. Is there a linux version or are you using wine?

If your using wine, under Applications->Wine->Configure Wine 
click on the Drives tab and click Autodetect... 

and if you see your disk then you should be good, if you don't manually add it with the Add... button and usually under /media/blank/ (fill in the blank with the name of the drive)

Hope this helps

---

### Post by windfix on 2008-11-13
There is a Picasa version for Linux, but I have been told that it uses Wine (not sure if that's accurate, you can install it direct from Google repository).  I used the autodect drives as you suggested, and it did add my home folder and root folder to the list, but no change in Picasa's behavior.

---

### Post by xc3RnbFO8P on 2008-11-13
Maybe you have to empty the temp folder in Wine?

---

### Post by windfix on 2008-11-13
> **Ringi said:**
> Maybe you have to empty the temp folder in Wine?

Can you tell me how?  I don't see anything under Configure | Wine.

I looked through the .wine folder in my home directory.  There is a folder at /.wine/dosdevices/c:/windows/temp  but nothing in there.

---

### Post by xc3RnbFO8P on 2008-11-13
/home/your folder/**.wine**/drive_c/windows/temp

---

### Post by windfix on 2008-11-13
Yeah, it's empty already.  No joy.

---

### Post by xc3RnbFO8P on 2008-11-13
Try to start Picasa from Terminal
> sudo picasa
see if it make some difference.

---

### Post by windfix on 2008-11-13
An excellent idea, wish I'd thought to try it.  Unfortunately, it launches Picasa as a different user (root), which loses all the albums and photos that "Paul" (me!) owns.

Added info:  Exporting seems to handle the first few Megs of the export, choking when it hits some particular filesize.  At original resolutions, it chokes after exporting about 4 photos.  At smaller resolution (600x800), it gets up to about 12.

Another piece of the puzzle:  When I browse for location to export files to, the directory tree uses "PicasaDocuments" rather than /home/Paul, the actual name of my home directory.  Is the program running as another user somehow?

---

### Post by xc3RnbFO8P on 2008-11-14
Did you check
/home/your folder/.picasa/drive_c/windows/temp/Picasa2/Picasa2 filecheck

---

### Post by windfix on 2008-11-14
That folder is also empty. :(

---

### Post by xc3RnbFO8P on 2008-11-14
> When I browse for location to export files to, the directory tree uses "PicasaDocuments"
 Screenshot?

---

### Post by windfix on 2008-11-14
Hopefully you can see it here:

[http://picasaweb.google.com/lh/photo/59WEiGaCiBzWVpBnRVCPNA](http://picasaweb.google.com/lh/photo/59WEiGaCiBzWVpBnRVCPNA)

The browse window's gotta be WINE, and the subfolders of "PicasaDocuments" (ie. audiobooks, desktop, etc.) are the same folders occuring under /home/paul

---

### Post by xc3RnbFO8P on 2008-11-14
Under the desktop icon is a harddisk icon with +
click on +
and find home and your folder.

---

### Post by windfix on 2008-11-15
Yeah, that is true, but the folder tree is same under /home/paul and under PicasaDocuments.  Attempting to export to a folder in either one gives the same error message.

---

### Post by xc3RnbFO8P on 2008-11-15
I think it is a Wine problem.
Uninstall from Synaptic (complete removal)
and reinstall it again.

---

### Post by windfix on 2008-11-15
Sorry, uninstall Wine or uninstall Picasa?

I am backing up all my photos and albums to external disk just in case.  Have also thought maybe I should try Picasa v.3 beta

ah - I think you meant wine, and since I don't use it for anything else, will start with that...

(after):  Same error message, tried exporting under PicasaDocuments and also under the Hard-disk Icon (again, file tree is same under both)

Time for a v.3 Beta upgrade?

---

### Post by xc3RnbFO8P on 2008-11-15
> 
Sorry, uninstall Wine or uninstall Picasa?
I am talking about Wine.

---

### Post by xc3RnbFO8P on 2008-11-15
> Time for a v.3 Beta upgrade?
Yes

---

### Post by windfix on 2008-11-15
Thanks, Ringi.  I'll try going with Picasa 3 Beta.  I am also going to move my Picasa backups to a different machine and try it on non-Apple hardware.  I've tried to work around Apple's proprietary nonsense in the interest of dual-booting OSX, but giving it up and going back to a Dell.

---

### Post by windfix on 2008-11-16
Follow up in case it's useful to others:

Moving Picasa albums in Ubuntu:

I struggled through moving my photos and albums between Ubuntu (Intrepid) machines and thought I'd post some notes for others that may be attempting.  Here's what worked:

In Picasa (2.7 in Ubuntu 8.10), use Tools | Backup Pictures; Make a new backup set, select everything.  Under Edit Set, use disk-to-disk backup and aim it at an external drive (USB in my case).  My photos were stored in /Home/username/Pictures to start.

Picasa created several folders:  $MyPictures, $Application Data; plus files.txt and an executable PicasaRestore.exe

Copy all 4 of those items to your home directory in the new machine.

Install Picasa and Wine using Synaptic if you haven't already.

Under Applications | Wine | Browse C: drive, navigate to /home/username and open PicasaRestore.exe

I chose to restore to original locations (the other option resulted in errors for me) and let it run the restore.  It took a long time, 13 GB of data.

Finally, I verified the photos were now under /Pictures and I deleted all 4 of the items of the backup including $MyPictures folder.  (if you do not, you wind up with duplicate photos in /$MyPictures and /Pictures)

The albums came through intact, which was really the whole point of not just transferring the files manually.

---

### Post by Arup on 2008-11-17
There is a Picasa for Linux which I have installed after enabling google picasa in the repos, it works flawlessly and doesn't need any WINE as its native x64 Linux. Its Picasa 3.0 beta and I followed instructions from  [http://www.ubuntugeek.com/how-to-install-picasa-30-beta-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-picasa-30-beta-in-ubuntu.html)

It recognizes my camera and downloads pictures automatically as set up, I also have no issues updating pictures to my Picasa account.

---

### Post by windfix on 2009-01-04
I realized after some tinkering that the export problem only occurs when Picasa is asked to export from within an Album.  Exporting from a folder works fine.  Not sure if that helps anyone, as finding and exporting the originals one-by-one defeats the whole purpose of the Albums, but it does work.

---

### Post by one51 on 2009-04-16
> **windfix said:**
> 
Under Applications | Wine | Browse C: drive, navigate to /home/username and open PicasaRestore.exe

I chose to restore to original locations (the other option resulted in errors for me) and let it run the restore.  It took a long time, 13 GB of data.

Finally, I verified the photos were now under /Pictures and I deleted all 4 of the items of the backup including $MyPictures folder.  (if you do not, you wind up with duplicate photos in /$MyPictures and /Pictures)

The albums came through intact, which was really the whole point of not just transferring the files manually.

An additional (though not so detailed) primer: I was copying a Picasa backup from Windows to Linux.  Unfortunately I had all my pics stored on the Desktop before, now wanted to copy them to the Pictures folder instead.  I had considerably more trouble.  Brief synopsis:

Copied the photos themselves manually, not using the backup tool.  But I used the backup tool to copy the albums, because manually copying the album files DOES NOT WORK (not any way that I tried to modify them, anyway).

Had to search and rename the photo location strings in each album's .pal file, using text editor (took 5 minutes once I figured out a method).  Now the albums would refer to the correct location of the photos, after restore.

Used the method above with Wine, with one caveat: at first I could not find where wine put the files, as it wasn't in the Picasa location (in my home account's .google directory).  I mapped the .google directory's c_drive home folder of my username to a drive using wine's config, and extracted the album files there.  Here is the folder where the albums end up,
~/.google/picasa/3.0/drive_c/Documents and Settings/one51/Local Settings/Application Data/Google/Picasa2Albums

Finally it worked.  But beware, because if you do it wrong, Picasa deletes the .pal files you've restored.

You may have to be logged into your google account for it to work, though I don't know.  I have a lot of albums online so I really wanted to make this work.  It only took 6 hours of fiddling!  :-)

---

