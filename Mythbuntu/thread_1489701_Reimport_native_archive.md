---
title: "Reimport native archive"
date: 2010-05-21
forum: Mythbuntu
---

### Post by MartinusEx on 2010-05-21
Hi Folks,

usually I reimport native archives from DVD or hard disk one by one.
The way ist
CD/DVD -> Archive files -> Export/Import to/from a medium
I need to reimport quite some videos that way
Doing this one by one is a pain. 

Since mythfrontend uses mytharchivehelper I assume that a command line is generated and a process of mytharchivehelper of it's own is spawned using the proper options.

I assume further, that using mytharchivehelper directly in a script might work to reimport 10 or 20 video including all the database stuff.

Has anyone an knowldege how to do this? 
(command line options of mytharchive(helper), is it possible at all?)
If yes could you please provide?!

Is there documentation on mytharchive/mytharchivehelper available?

Thx a lot in advance

Martin

---

### Post by MartinusEx on 2010-05-21
Hi Folks,
me again.
I'm at best when I'm forced to articulate my problems in a question.
I solved it my self, see attached script file and batchimport example file
Actually it works teh way I assumed:
Writing an export of a recording to any medium (HD or DVD) with mytharchivehelper generates an XML file with the name of the video file plus the .xml extension

mytharchivehelper uses option -f to define the xml-file as import source and a channelid to link it to.
And very nicely imports the so defined recording back into mythtv database and the recordings folder

the attached shell script opens the batchimport file and imports every recording stated there back into mythtv

You should hav a look inot the script. It is well possible that you need to edit the base directory of the batchimport file

Questions?
Ask!:popcorn:

thanks for visiting

Martin

---

### Post by CodeOptimist on 2010-09-29
Thanks so much for this script, Martin! I was trying to import a large number of native show archives into a fresh install of MythTV and some googling led me to your post. After I changed the script a bit to reflect my directory setup it worked perfectly!

---

### Post by MartinusEx on 2010-09-29
You're very welcome

Martin

---

