---
title: "Seeking advice from experienced F-SPOT users"
date: 2009-04-05
forum: Multimedia Software
---

### Post by heitjer on 2009-04-05
Hi All,
I just setup my main machine with Linux after years of Windows usage. I started out with Kubuntu because I really wanted DigiKam and the tie in with the Desktop. Although I liked the desktop it did not feel "right", maybe because I used ubuntu gnome on my Laptop before. Anyhow I know that I can use digiKam on Gnome but now I found F-Spot and it seems to be really quick and easy. 

Before I now start with sorting and tagging photos I really like to see what would be a really good setup for me. 

Here is my environment. To date I have been storing all photos on a central LINUX server running Samba. The entire family is able to access the files which are stored but I typically have only write access. We have multiple OS's (Win, Mac OSX, Linux).

SERVER
--DOCUMENTS
--PICTURES
---YEAR
----FOLDER

Before placing pictures on the server all pictures are renamed to "090321-wedding001" (YYMMDD-description-3 digit counter), all folders are also named "090321-wedding". Currently I have about 8 years of pictures and folders on the server in about 40GB.

I noticed that F-Spot is trying to copy all pictures in a folder on the home directory. 

Questions:

[LIST=1]
[*]What would be your recommendation on how I should set this up?
[*]Should I keep a folder on my hard drive and just mirror it out to the network for family members?
[*]When I use my hard drive for F-Spot I do not see how others could easily browse by 'tags', any idea? 
[*]When I point F-Spot to a mounted folder on the network instead of a home folder I could possibly see this working. thoughts?
[*]When I tag photos in F-Spot would other machines on the network be able to browse the tags? Or would they be needing access to the F-Spot database?
[/LIST]

Your thoughts are much appreciated!

---

### Post by lovinglinux on 2009-04-05
If you need to share tags between users then you should use a program that can manipulate IPTC, which basically means the tags will be embedded in the image files as metadata and could be read by any program with IPTC support.

DigiKam certainly can do that. I'm not sure about F-Spot, but I believe the tags are stored on a database.

---

### Post by heitjer on 2009-04-05
[Quote from F-Spot]("http://f-spot.org/User_Guide/Organize#Tag")
Expert Tip: F-Spot can write tags as metadata fields into JPEG files. Tags for various RAW files, PNG, TIFF, and others are written to F-Spot's database. You will have to re-tag these files if you re-import your collection.

95% of my photos is JPG so I should be fine.I do not like to get the RAW files tagged anyway as I keep copies with the same name as JPG files. 

Question - when I use F-Spot on my machine and then copy folders to the Server these tags are the search-able by other programs (i.e. iTAG for Windows) - correct?

---

### Post by lovinglinux on 2009-04-06
> **heitjer said:**
> Question - when I use F-Spot on my machine and then copy folders to the Server these tags are the search-able by other programs (i.e. iTAG for Windows) - correct?

I don't think so. I thought that being able to write the tags as metadata only into jpgs a little bit strange, so I did a test. It appears that F-Spot tag are only readable by itself.

There is an alternative tho. Picasa is a simple and beautiful photo manager, which is ideal for your family needs. It can write metadata as IPTC and you can install on Windows and Linux. To browse photos by keyword, use Picasa's search feature. Since the tags are written into IPTC fields, then can be viewed by other IPTC programs like iTag and Digikam.

To install Picasa you can add the Google repository. See instructions at [http://www.google.com/linuxrepositories/ubuntu704.html](http://www.google.com/linuxrepositories/ubuntu704.html)

The instructions says it is for Ubuntu 7.04 but it works on Hardy, so I guess it should also work on Intrepid.

---

### Post by heitjer on 2009-04-06
Thanks - I looked at this last night and already send my daughter a link to evaluate. She's the creative one...

From what I can gather picasa is also gathering all photos in one spot. 

Can someone confirm:

[LIST]
[*]when I set this up on my Linux machine I choose a folder on the network (mounted) and choose "scan always" - this folder would be pointed to my already existing folder on the server
[*]then I work the tags and ensure tagging is done for all photos
[*]then I install picasa on my families machines (Win & Mac) and point to the same network folder.
[*]all should only have "read" access so they can not mess up the tags
[/LIST]

---

### Post by heitjer on 2009-04-06
I think I am getting into picasa although it stilllacks the real networking ability. 

Here is a good post: [Link]("http://www.google.com/support/forum/p/Picasa/thread?tid=20a1baeae4557e0f&hl=en")

I think as long as all other server users are "read only" this will work as the main database is kept on the main machine.

---

### Post by heitjer on 2009-04-06
Pull for F-Spot:
[LIST]
[*]I prefer the easy tagging in F-Spot over the one in Picasa.
[/LIST]


Pull for Picasa:
[LIST]
[*]I like the easy, quick & feature rich editing in Picasa
[/LIST]

I add more bullets as I find more interesting things.

---

