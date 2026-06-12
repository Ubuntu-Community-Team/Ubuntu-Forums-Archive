---
title: "Problem with Ubuntu or amazon mp3 downloader?"
date: 2009-09-18
forum: Multimedia Software
---

### Post by virgoboy on 2009-09-18
Hi Folks! I purchased an MP3 from amazon the other evening. All seemed well with the download (via FF 3.0) however, when i go to open the File Download folder, which should contain the actual MP3 file, the folder is empty. Firefox appears to download the track and the amazon software appears to be processing it but there is nothing there.
 
This started after a few updates the day or so before via Synaptic. I'd like to figure this out as there are Several albums worth of songs i would like to purchase via amazon.
 
Thanks in advance!:P

---

### Post by irv on 2009-09-18
> **virgoboy said:**
> Hi Folks! I purchased an MP3 from amazon the other evening. All seemed well with the download (via FF 3.0) however, when i go to open the File Download folder, which should contain the actual MP3 file, the folder is empty. Firefox appears to download the track and the amazon software appears to be processing it but there is nothing there.
 
This started after a few updates the day or so before via Synaptic. I'd like to figure this out as there are Several albums worth of songs i would like to purchase via amazon.
 
Thanks in advance!:P

It is very possible that your FF Download's are going somewhere else. I have my set to download to my Desktop. Goto your Edit>Preferences and under the Main tab see where Download save files are set to go.

---

### Post by virgoboy on 2009-09-18
Seems like the download is Stuck in Firefox.  I have a screen shot but i am unsure of how to include it here.  The amz file is still in the download area (queue?) of the browser and i am unable to Open it.

---

### Post by irv on 2009-09-19
> **virgoboy said:**
> Seems like the download is Stuck in Firefox.  I have a screen shot but i am unsure of how to include it here.  The amz file is still in the download area (queue?) of the browser and i am unable to Open it.

The Download queue are you are refering to is just the tmp folder. If you right click on the file you downloaded and then select view in location, you can copy or move it from there to where ever you want. You should be able to run it right from there is you like also.
[ATTACH]129076[/ATTACH] [ATTACH]129077[/ATTACH]

---

### Post by irv on 2009-09-19
To take a screen shot just goto Applications> Accessories>  Take Screenshot. Next when you want to post the screenshot just click on the paper clip and then browse for the file and attached it to the post.
Follow this screenshots.
[ATTACH]129073[/ATTACH] [ATTACH]129074[/ATTACH] [ATTACH]129075[/ATTACH]

---

### Post by virgoboy on 2009-09-19
Thanks, Irv.  I appreciate your help.  All of the right-click options are greyed-out except Copy Download Link, Select All (both of which don't do anything) and Remove From List.  I'm stymied as i have never seen this happen before in Firefox, regardless of the OS:confused:

---

### Post by irv on 2009-09-19
From looking at your screen shot, it appears to be a issue with Amazon website.The query you were talking about is on there website. It is not a firefox issue. I am not sure how to fix this problem because I do not have account with Amazon to download MP3 files or what ever format they use. I wish I had an answer, but I don't. Sorry.

---

### Post by virgoboy on 2009-09-19
Yep, that's why i posted it here as i couldn't tell if it was a problem with amazon, firefox or ubuntu.  Thanks for your help!:)

---

### Post by mkarl on 2009-09-19
Hi,

To open the AMZ file, you need the Amazon MP3 Downloader.  I encountered a similar problem previously in which it was saving the AMZ file but was not launching the downloader.  Perhaps this is what you are experiencing? I seem to remember this page fixed it:

[http://www.amazon.co.uk/gp/dmusic/help/amd.html/ref=dm_gs_amd](http://www.amazon.co.uk/gp/dmusic/help/amd.html/ref=dm_gs_amd)

using the link in the troubleshooting section:
"If you have already installed the Amazon MP3 Downloader, click here to enable it for use with this browser."

Its a long shot, and I don't know if this is the same problem you're experiencing, or just a similar one.

Karl :)

---

### Post by irv on 2009-09-19
> **mkarl said:**
> Hi,

To open the AMZ file, you need the Amazon MP3 Downloader.  I encountered a similar problem previously in which it was saving the AMZ file but was not launching the downloader.  Perhaps this is what you are experiencing? I seem to remember this page fixed it:

[http://www.amazon.co.uk/gp/dmusic/help/amd.html/ref=dm_gs_amd](http://www.amazon.co.uk/gp/dmusic/help/amd.html/ref=dm_gs_amd)

using the link in the troubleshooting section:
"If you have already installed the Amazon MP3 Downloader, click here to enable it for use with this browser."

Its a long shot, and I don't know if this is the same problem you're experiencing, or just a similar one.

Karl :)

Karl,
This link is for a windows; exe file. Do they support Linux with there downloader?

---

### Post by mkarl on 2009-09-19
The attached image is as I see the page.

The link I'm referring to is the word 'here' on the right.  AFAIK it doesn't link to an EXE, but I can't tell as it just takes me back to the MP3 store again, but I assumed this was because it was already enabled with my copy of firefox. Does it simply link to an EXE for yourself?

Karl.

---

### Post by irv on 2009-09-20
> **mkarl said:**
> The attached image is as I see the page.

The link I'm referring to is the word 'here' on the right.  AFAIK it doesn't link to an EXE, but I can't tell as it just takes me back to the MP3 store again, but I assumed this was because it was already enabled with my copy of firefox. Does it simply link to an EXE for yourself?

Karl.

Thanks Karl, that should help virgoboy.

---

### Post by SuperSonic4 on 2009-09-20
> **irv said:**
> Karl,
This link is for a windows; exe file. Do they support Linux with there downloader?

Yes there is a deb version available but beware that you'll need the dependencies yourself. This is more relevant in 64bit because the downloader is 32bit

---

### Post by virgoboy on 2009-09-20
Sorry guys, this did not seem to change anything.  I'm going to contact amazon directly today by phone... wish me luck and if the problem has been fixed, i'll post it here!

---

### Post by virgoboy on 2009-09-20
RESULTS!!  By clearing both my Private Data (including Cookies) and the previous amz files in the FF tmp folder and uninstalling the MP3 Downloader software, i and amazon got it working OK!  We'll see what happens next but it's a beautiful thing, so far.

Thanks again for all of your help!:P

---

