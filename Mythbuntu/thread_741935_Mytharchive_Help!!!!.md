---
title: "Mytharchive Help!!!!"
date: 2008-04-01
forum: Mythbuntu
---

### Post by browndog289 on 2008-04-01
Hello

I am having trouble with mytharchive.
My mythtv hard disk is 91% full so I am looking to free up some space - so I thought I would create a DVD with some of the recordings so I can delete them from the disk. However when I go into mytharchive any files that have been transcoded into xvid (MPEG-4) show up as 0Kb, if I continue to write a DVD the log file stays up and does not progress - I stopped it yesterday (31/03) as it was still there from 21/03!! I had to delete the .lck file in order to use mytharchive again. Thats problem 1.

As it wouldn't record to DVD I thought I would try creating a native archive - it let me choose the recordings and they showed up as their correct size so I continued and it burned them to disc. Hooray! I thought, but then the problem began when I wanted to play the native archive disc in myth - I can't find out how to do it. I have archive settings and then play recorded disc but that won't work neither will play DVD so I am back to square one with my myth hard disk getting more full by the day with no way to archive the recordings!

Can anyone help?

---

### Post by ahood on 2008-04-01
I don't think I have the solution to your problem; however, working together and input from a few others, I am hopeful that an answer can be found.

First, a bit more information is needed. 

What are the resolutions of the original recordings (480x480, 720x480, other)?

What is the content of the mythburn.log file? 
This file is located in the directory where the temporary files are located. Pasting the contents of this file is highly recommended.

Are you transcoding the recordings during the archive process?
Transcoding is enabled when selecting SP, LP, or other option of Mytharchive. If "Don't Re-encode" is selected, then transcoding is disabled during the archive process.

Do you have a file called .ICEauthority stored in the user home directory?
This file is created automatically by some applications written to run in a KDE environment and can disrupt Mytharchive.

Don't despair. Have faith and keep researching for the solution.

---

### Post by browndog289 on 2008-04-02
Hello,

I am encoding the recordings in PAL with a size of 720x576.
There is a file in my user directory called .ICEauthority but I have set it to be deleted in the myth startup script.

After a recording is made it is transcoded into MPEG4 to save space.

I am transcoding to SP DVD during the recording but most recordings show up on the bar on the right (showing how much space is used on the DVD) as 0Kb.

MYTHBURN.LOG is attached to this post.

---

