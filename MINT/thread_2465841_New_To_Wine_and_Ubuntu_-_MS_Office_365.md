---
title: "New To Wine and Ubuntu - MS Office 365"
date: 2021-08-12
forum: MINT
---

### Post by michaelmacho on 2021-08-12
Hello Everyone

I am new to using Linux as my daily driver OS.  Just 4 days ago Windows took a crap with an update and Microsoft did not call for 4 days.  I finally got so frustrated as a Microsoft Partner that I formatted my machine and installed Linux.  I had been thinking about doing this for some time and watched many You Tube videos on the best way to do this and make life easy again.  Anyways I am on day 3 of using Mint Linux with Ubuntu and I have managed to accomplish a lot.  

I did install the paid version of Wine called Cross Over after watching a video on you tube that discussed what Wine is etc.  I then installed Office 365 with the latest version of Cross Over and the latest version of Mint Linux.  All updates have been done to Linux and Cross Over. 

I am not able to get outlook working, however that is not as big a deal as i discovered and installed Thunderbird to work with our corporate exchange server and downloaded many nice plugins for Thunderbird, so as of today email seems ok.

My real issue is with Word processing and Excel and PowerPoint all of which have been daily drivers for me for over 25 years.  I got each of these programs working with Cross Over, and i have come to discover that opening a file using word in the File Menu does not work and opens a blank page.  I then go directly to the file in the file manager in Linux and open it and sometimes it opens and many times it still opens with a blank screen.  I was hoping that someone has a similar issue and solution.   It would be nice to be able to open the files directly from Word and not go through massive tree structures of files 15-20 deep just to find a file that may or may not be the correct file.  

I did see Libre Office - But it has a real issue with opening complex documents etc.  Not to mention it is just very different in terms layout etc.  Perhaps one day I can covert over completely.

I just cant seem to figure out how and why my existing documents will not open.  Simple documents with 1 or 2 pictures are a problem.  

I did manage to figure out how to Sync my cloud One drive account with Linux R Clone and it is working great.  

Any help would be great.

Overall I am really enjoying Linux.

Thank you 
Michael

---

### Post by howefield on 2021-08-12
Thread moved to the "*MINT*" forum.

---

### Post by monkeybrain20122 on 2021-08-12
Isn't it true that you can use  a web version of MS office if you have an outlook/hotmail account?

---

### Post by michaelmacho on 2021-08-12
Yes there is a web version you can also configure to use OUTLOOK look or other mail clients.  What does this have to do with Wine and Microsoft Word and opening files etc. 

Web versions of word are not the same and have limited functionality and are harder to use as a daily driver.  Those are used more for collaboration and to compete with G Suite.

---

### Post by monkeybrain20122 on 2021-08-12
> **michaelmacho said:**
> Yes there is a web version you can also configure to use OUTLOOK look or other mail clients.  What does this have to do with Wine and Microsoft Word and opening files etc. 

Web versions of word are not the same and have limited functionality and are harder to use as a daily driver.  Those are used more for collaboration and to compete with G Suite.

Wine is a hit and miss that is never guaranteed to work. It also depends on your version of Office and the version of wine. Maybe you can get some info about what works in WineHq's list, but the list is kind of outdated and old so it might work even if the list says it doesn't and vice versa.  You can control the wine version with PlayOnLinux so if there is some version of wine that works with your version of Office (with Platinum or Gold rating) then you are home free. Just create a wine prefix in playonlinux with the version of wine that works. Playonlinux is in the Ubuntu repository so it should also be in Mint's.

If nothing works and if you have at least 6 G of ram (and a Windows installer) you can set up a minimalist VM for Windows and install Office in there, that will definitely works, guaranteed. Virtualbox is quite easy to set up.

---

### Post by michaelmacho on 2021-08-12
Hi 
Thank you for the reply.  I actually have already setup Oracle Virtual Box VM and installed windows on that in order to use it if needed or if i need to reference it in order to manage tech support of my company.  I would really really like not to have to use Windows as little as possible.  

I saw 2 you tube videos with the exact version of Cross Over and office 365 work yesterday online.  Again the applications work and open as a program, you can create new documents that are complex in structure and open them with no problem.  It is the existing documents that are an issue.  about 5 years ago others using office and wine had similar issues based on the forums i have read.  

I figured by now it would be working or have some work around.  

If we cant get this to work with Office 365 to open existing files, then I will look into going down a few versions to Office 2019 and see if that helps.  \

Any thoughts ?

Thank you for your help.

---

### Post by monkeybrain20122 on 2021-08-12
Well I don't really know. I don't use MS Office and I am not a big wine user. Your question actually belongs in the Wine subforum rather than here since it really has nothing to do with Mint. I am sure wine works the same way in both Ubuntu and Mint, and if differences do exist those would be trivial. I think there is more traffic in the wine subforum and you are more likely to get an answer there. It seems nobody really visit this part of the forum except people who are bored or procrastinating on other stuffs like me. :)

---

### Post by michaelmacho on 2021-08-13
Can you move this to the WINE forum 
it was suggested to do that.  

As a new user i am not sure i am able to do this.

---

### Post by monkeybrain20122 on 2021-08-13
> **michaelmacho said:**
> Can you move this to the WINE forum 
it was suggested to do that.  

As a new user i am not sure i am able to do this.

You have to ask a moderator to do that.  So click "report post" at the lower left hand corner of your first post and then explain the reason.

---

### Post by wildmanne39 on 2021-08-14
Hello michaelmacho and welcome to the forum, since you use Mint Linux your thread belongs here and as for our volunteers seeing your post I believe most of them use the activity stream to view new posts, so the best way to get your thread seen is to bump your post once every twelve hours to keep it in view of the volunteers here.

[https://ubuntuforums.org/activity.php](https://ubuntuforums.org/activity.php)

---

### Post by michaelmacho on 2021-08-14
DUMB Question:  To bump the post every 12 hours do i just add to the tread or click on report post?  I don't really see any other option for bumping a post.

---

### Post by wildmanne39 on 2021-08-14
Just write bump in a post in your thread and click the submit reply button.

---

### Post by T6&amp;sfpER35% on 2021-08-14
if i  were you i'd just forget about WINE and learn how to use Libre office instead.
maybe it's just me ,but i didn't install Linux just so i could try running Windows programs in it (it's not safe either,btw)
i have never encountered a document or whatever that Libre office couldn't handle, and i get tons of emails/docs from windows users 
same goes for sending docs with Libre office to windows people , might want to tweak it here and there before sending ,but no1 has ever come back to me saying they can't open docs.

---

### Post by QIII on 2021-08-14
Hello.

Given that the WINE sub-forum is in a section with the tag line 

> **Ubuntu Specialised Support**
Specialised categories of support for the recognised Ubuntu flavours: Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, Ubuntu Studio, Mythbuntu, Ubuntu Mate, Ubuntu Budgie and Ubuntu Kylin.

your question regarding WINE on MINT belongs ing the MINT sub-forum, to which is was moved by another Admin.  MINT is not Ubuntu and, since the MINT developers are free to do as they choose, it is not necessarily the case that a solution that works for Ubuntu will work for MINT.  Generally things are the same, but specifics may differ.

Accordingly, the thread will remain here.

---

### Post by michaelmacho on 2021-08-14
OK  Thanks.  It was recomended that we move it to the WINE sub forum ...  What ever you think is best thank you

---

### Post by CharlesA on 2021-08-14
> **3nd said:**
> 
maybe it's just me ,but i didn't install Linux just so i could try running Windows programs in it (it's not safe either,btw)

What do you mean by "it's not safe either"?

---

### Post by michaelmacho on 2021-08-14
Thank you for everyone's help based on the feedback i discovered it was a permissions issue with the files.  Since I setup R Clone with One Drive and Google Drive i had to set the permissions to folders and files.  Once you set all the various permissions you are able to open files directly from the location and also from the File OPEN menu in Word, Excel or PowerPoint.

---

### Post by TheFu on 2021-08-14
> **michaelmacho said:**
> Thank you for everyone's help based on the feedback i discovered it was a permissions issue with the files.  Since I setup R Clone with One Drive and Google Drive i had to set the permissions to folders and files.  Once you set all the various permissions you are able to open files directly from the location and also from the File OPEN menu in Word, Excel or PowerPoint.

Files and directories in your HOME should be owned by your userid, nobody else.

If the plan is to have a shared system with WINE and programs that run under it that everyone in the office can use, there are many different ways to run programs on the other machine, but have just that window displayed on your local PC. No rdp/vnc needed. It is built-into X/Windows to do these things and has been for 40 yrs.

If you need to have documents shared by multiple users, there are commonly used methods using Unix groups to make that available where everyone can edit the same file. Some tools see that multiple people have the same file open and show the updates live.  I don't think LibreOffice does it.  Mastering Unix permissions isn't hard, but it does take 45 minutes of concentrated effort to get there.  Without that understanding, there will be hours, days, weeks, months of frustration over dumb permissions stuff that is trivial corrected. All Unix-like OSes use the same model for permissions, so this skill is useful for every popular OS you will use, except 1 (which you can guess).

While it might be preferable to use LibreOffice long-term, often businesses need to use the same tools that their clients use. In a business, it isn't worth having incompatibilities.

When I pay for software, I'm going to call their support line for help if there are issues.  That's why we pay for software - support.

---

