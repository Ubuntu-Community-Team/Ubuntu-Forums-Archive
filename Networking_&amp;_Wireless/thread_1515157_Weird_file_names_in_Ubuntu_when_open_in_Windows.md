---
title: "Weird file names in Ubuntu when open in Windows"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by WanderingOtaku on 2010-06-21
Hello everyone,

I am having an odd issue with some files and folders that are on my Ubuntu computer when looking at them in windows.

To start, I am running Lucid on the drive with the files I am looking at. I am looking at them in Windows 7, but can confirm the same issue happens in Windows XP. The server is shared via samba, and I can see and access files from either OS just fine.

The issue is with the names. What happens is that the files and folders that have names with special characters such as a colon ( : ) show up as gibberish (ex: G683EG~E). See below to see what I am seeing in Windows.

[IMG]http://imgur.com/73I04.png[/IMG]

Now, I could just rename the folders and files without the characters. The reason I don't is that I need them to be that way due to using XBMC. They need to match up with an online database (thetvdb.com). Sometimes, when I can't use that computer, I'd like to get to those files on my Windows computer.

Does anyone have any ideas on what to do to make these folders show up right in Windows? I realize this isn't really an issue with Ubuntu as they show up perfectly there. I thought I would give it a try...

---

### Post by amauk on 2010-06-21
What you're seeing is the short filename (the old DOS 8.3 name)

this is probably because (AFAIK) you cannot use colons in filenames under Windows
so the DOS short name is used as a fallback

No idea if it's fixable, sorry

---

### Post by yetiman64 on 2010-06-21
I'm pretty sure that amauk is right re. DOS renaming of folders/files as Windows can't handle some Linux used characters (hence the changes).

What I did when dual booting Win and Ubuntu was to go into Ubuntu when such a character was noted, use the nautilus search function to find all instances of that character, then manually replace all instances with a Windows friendly character. Reboot back into Win and check the names etc. It worked for me but did take quite some time. 

Searching and replacing such characters in Linux should be possible with some sort of scripting, but is a bit beyond my experience with scripting as such. Someone else here may be able to help with that idea.

Edit: Just noted the online database reference, this makes things much more complicated for any changes.

---

### Post by WanderingOtaku on 2010-06-22
Thank you both for the reply.

Yeah. Im certain that all the offending folders just have a colon in it, as well as the files inside. Renaming them isnt a problem, as I can just use krename on all the files real quick, it is just they need to match the online database. I think I know a way to make it so I don't have to have the file names matching, but it'll take some work to get it right. 

I was curious if there was a way to get it working in Windows without having to do any workaround on the Ubuntu computer, but that may not be possible.

---

### Post by lisati on 2010-06-22
I suspect that the old-style 8.3 filename format is being used because the colon has a special meaning in some file systems, e.g. in C:filename.txt the colon separates the drive letter from the filename itsself.

---

### Post by amauk on 2010-06-22
One hacky way of overcoming this might be using 2 separate folders
One for native Linux
and a second one for your Samba share

Native folder contains the "real" files
and fill the samba share with links to the "real" files / folders, and give the links windows-friendly names

You should be able to script it so that these links are created automatically

---

### Post by WanderingOtaku on 2010-06-22
I'll have to look into how to do that. It sounds like a good solution, if I get it working.

Thanks.

---

