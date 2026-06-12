---
title: "How do you change video cover art?"
date: 2013-01-28
forum: Mythbuntu
---

### Post by nhtrader on 2013-01-28
MythTV v0.25.3-32
ubuntu 12.04 LTS
Theme: MythCenter Wide 1.6


I added a video to the library and pressed "e" to edit the title (to make it exact) and then pressed "w" to find the cover art. However, a list appeared (several entries with the same title). So I picked one; the wrong one. And now I can't undo this selection and replace the cover art for this movie.

I have tried the following:
1. deleting the movie/video from the DIR /var/lib/mythtv/videos
2. deleting the cover art from DIR /var/lib/mythtv/coverart
3. opening the Myth Frontend and pressing "m" and selecting rescan.
4. exit Myth Frontend
5. re-copy the video to /var/lib/mythtv/videos
6. re-open Myth Frontend 

And when I select video library two things happen...
1. It displays the video (without rescanning. (note that I deleted the movie and rescanned the library without it and yet it still appears)
2. It still displays the wrong cover art (remember I deleted it from the cover art DIR. That jpg no longer exists.)

How do I replace the wrong cover art for this title?

---

### Post by josephmills on 2013-01-28
I made you a video Hope it help :) 

Changing fanart in Ubuntu TV and MythTV
Uploading your video. 7 minutes remaining. Your video will be live at: 

**EDIT** 

Here it is all uploaded 

[http://www.youtube.com/watch?v=yvZNn6qNRvQ](http://www.youtube.com/watch?v=yvZNn6qNRvQ)

---

### Post by ajgreeny on 2013-01-28
I do not use, nor know MythTV, but I would guess that those configuration details are kept in some hidden folder in the /home of the user who made the choice, so have a good look in your home with all hidden files and folders showing (Ctrl+H).

To see all possibilities it may be worth running ```
locate -i myth | grep $USER
``` for a list of all files and folders containing upper or lower case "myth" in the name.

---

### Post by larsolav on 2013-01-28
> **nhtrader said:**
> MythTV v0.25.3-32
ubuntu 12.04 LTS
Theme: MythCenter Wide 1.6


I added a video to the library and pressed "e" to edit the title (to make it exact) and then pressed "w" to find the cover art. However, a list appeared (several entries with the same title). So I picked one; the wrong one. And now I can't undo this selection and replace the cover art for this movie.

I have tried the following:
1. deleting the movie/video from the DIR /var/lib/mythtv/videos
2. deleting the cover art from DIR /var/lib/mythtv/coverart
3. opening the Myth Frontend and pressing "m" and selecting rescan.
4. exit Myth Frontend
5. re-copy the video to /var/lib/mythtv/videos
6. re-open Myth Frontend 

And when I select video library two things happen...
1. It displays the video (without rescanning. (note that I deleted the movie and rescanned the library without it and yet it still appears)
2. It still displays the wrong cover art (remember I deleted it from the cover art DIR. That jpg no longer exists.)

How do I replace the wrong cover art for this title?

This is what I have done in the past after selecting the wrong suggestion in the list you initially saw: Highlight the video in the library, press "i" you should get a menu pop up (not in front of the computer now), I think under edit information or something like that there is a choice to remove/reset the downloaded metadata and art. Once you have done that,select the video and press w and select another option in the list of titles it gives you. If this is the wrong one, just remove/reset again and repeat until the right info pops up....

Cheers!

---

### Post by nhtrader on 2013-01-28
> **josephmills said:**
> I made you a video Hope it help :) 

Changing fanart in Ubuntu TV and MythTV
Uploading your video. 7 minutes remaining. Your video will be live at: 

**EDIT** 

Here it is all uploaded 

[http://www.youtube.com/watch?v=yvZNn6qNRvQ](http://www.youtube.com/watch?v=yvZNn6qNRvQ)

Wow that was fantastic. I watched your video twice. Nice job.

It was great to see how you were able to change/edit the cover art. However, it also demostrated how the various flavors of installation differ. Here's how it differs for my Theme:

1. When you opened the video options window, I noticed that you didn't explain what key you used to get this window to appear. In my implementation of MythTV I use a different theme and therefore the Video Options Window does not appear.

2. I also don't have a manage details windows and therefore can't reset details.

3. Since I can't reset details, I also can't retrieve details. But there exists a Retrieve All Details option when I press the "m" key. (BTW, hen I use this option, press "m" | Retreive All Details | nothing happens. No changes are made)

4. The way you arrive at Edit Details also differs, I do this by simply pressing "e" 

5. Your edit screen looks different from mine. Mine has a FIND ONLINE button rather than a search button and when I select it, MythTV presents three images which are still wrong. 

6. And while I'm in the edit screen, and I continue along to the coverart checkbox, which looks exactly like yours. All coverart that exists on my system appear just like it did on your video. However, I do not wish to use any of the other titles art work that exist on my PC. I want to fetch the correct art work from the web. This step was missing.

Your demonstration was helpful and showed a number of differences between themes and installation implementations which only illustrate the difficulty for users.

If you know how to remove the connection between MythTV's database and library file and explain that, it would be helpful because it would teach me how to restart the process of adding a new video to the library.

As it stands, I cannot get MythTV to erase the existing connection. So I can't make any changes to the coverart. Currently, when I use the "w" key, nothing happens. I cannot get a window to appear that presents me the original list of 7 choices for the video. I cannot get MythTV to treat this video as a new video (even after deleting the video file and the coverart and restoring them). Now when I press the "w" key - nothing happens; no choices appear. And no changes can be made.

I'm trying to find a way to remove an entry in the library so that I can restart the process of adding the video. Currently, there is a lingering link within MythTV that doesn't allow me to re-add the video to the libary.

Thank you again for the video.

---

### Post by nhtrader on 2013-01-28
> **larsolav said:**
> This is what I have done in the past after selecting the wrong suggestion in the list you initially saw: Highlight the video in the library, press "i" you should get a menu pop up (not in front of the computer now), I think under edit information or something like that there is a choice to remove/reset the downloaded metadata and art. Once you have done that,select the video and press w and select another option in the list of titles it gives you. If this is the wrong one, just remove/reset again and repeat until the right info pops up....

Cheers!

Yes. The 'i' key worked. Now I could see the Reset Details Option and use it.
Now after resetting the entry I could try other artwork. 

Thanks.

---

### Post by topcat5 on 2013-01-30
> **nhtrader said:**
> 

As it stands, I cannot get MythTV to erase the existing connection. So I can't make any changes to the coverart. Currently, when I use the "w" key, nothing happens. I cannot get a window to appear that presents me the original list of 7 choices for the video. I cannot get MythTV to treat this video as a new video (even after deleting the video file and the coverart and restoring them). Now when I press the "w" key - nothing happens; no choices appear. And no changes can be made.

If you manually moved files to your video directory, then make sure that the files have the correct permissions and ownership.  Usually this would be 0644 mythtv.mythtv  (or whatever ID is running the BE)  If this isn't correct, it will prevent you from being able to delete videos from the system.

I believe the system keeps the info in the DB. If you are familiar with SQL you could simply delete it from there.

---

### Post by nhtrader on 2013-01-31
> **topcat5 said:**
> If you manually moved files to your video directory, then make sure that the files have the correct permissions and ownership.  Usually this would be 0644 mythtv.mythtv  (or whatever ID is running the BE)  If this isn't correct, it will prevent you from being able to delete videos from the system.

I believe the system keeps the info in the DB. If you are familiar with SQL you could simply delete it from there.

Thank you for this detail. 

I did exactly as you described. I moved the files around and did not change the owner:group nor permissions.

The good news is that the 'i' key functionality worked despite my transgressions.

---

