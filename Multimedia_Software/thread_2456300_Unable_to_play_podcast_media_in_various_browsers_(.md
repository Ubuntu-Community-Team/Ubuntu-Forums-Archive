---
title: "Unable to play podcast media in various browsers (Chrome, Firefox) [Ubuntu 20.10]"
date: 2021-01-08
forum: Multimedia Software
---

### Post by tdog66 on 2021-01-08
OS: Ubuntu Mate 20.10; Kernel: Linux 5.8.0-36-generic; Architecture: x86-64


Browser 1: Google Chrome: Version 87.0.4280.141 (Official Build) (64-bit)


Browser 2: Firefox: Version 84.0.2 (64-bit)
----------------------


**Problem**: for the past week and a half, I’ve been unable to play various podcasts within either my Google Chrome browser, or my Firefox browser (see OS, kernel and application versions above). To be clear, the podcasts do not play at all. 


As you can see from the examples and URLs below, I was unable to play the same podcast using either Google Podcasts or Apple Podcasts in a browser environment. Moreover, these problems continued regardless of whether I was attempting to play the podcast (of either type) in Google Chrome or Firefox. I've included the relevant playback error messages below in the examples section. 

Separately, I also attempted to play the podcasts below on different podcast websites (Stitcher and Spotify Podcasts) -- but they didn't play at all on those either. Meanwhile, using my Plex web player (embedded within Chrome), the podcasts also did not play --- and I received the onscreen message "*Error code:h4 (codec)*."


Because the issue does not appear to be browser-dependent, I’m suspecting it’s OS and/or codec related. 


Just to make sure, I completely uninstalled *ubuntu-restricted-extras*, and then reinstalled *ubuntu-restricted-extras*, and finally rebooted – but this didn’t fix the podcast playback problems either. 


I checked various logs (syslog, dmesg, etc.), but nothing seemed amiss. I also checked the Google Chrome debug log at *~/.config/google-chrome*, but didn’t see anything. Are there any other important logs to check?


One other important note: while I experienced problems with roughly 25 different podcasts tested, there WERE some Google and Apple podcasts that DID play with no problems within both my Chrome and Firefox browsers – which again suggests an OS or codec issue. 


Please advise, thanks. 
---------------------------------


------------  **Examples** ------------------


** **Example 1 - Podcast: “Hacks on Tap”** URL: [https://bit.ly/3sadhrZ](https://bit.ly/3sadhrZ) **(Google Podcasts)**


Chrome Browser –> Onscreen play error message: “Something went wrong.  This episode couldn’t be played. Please try again later.”


Firefox Browser –> Onscreen play error message: “Something went wrong.  This episode couldn’t be played. Please try again later.”


**** Example 2 - Podcast: “Hacks on Tap”** URL: [https://apple.co/3s40aIW](https://apple.co/3s40aIW) **(Apple Podcasts)**


Chrome Browser –> Onscreen play error message: “Failed to load because no supported source was found.”


Firebox Browser –> Onscreen play error message: “The media resource indicated by the src attribute or assigned media provider object was not suitable.”


**** Example 3 – Podcast “The Daily”** URL: [https://bit.ly/2LvSrCO](https://bit.ly/2LvSrCO) **(Google Podcasts)**


Chrome Browser –> Onscreen play error message: “Something went wrong.  This episode couldn’t be played. Please try again later.”


Firefox Browser –> Onscreen play error message: “Something went wrong.  This episode couldn’t be played. Please try again later.”


**** Example 4 – Podcast “The Daily”** URL: [https://apple.co/2Xlj3Je](https://apple.co/2Xlj3Je) **(Apple Podcasts)**


Chrome Browser –> Onscreen play error message: “Something went wrong.  This episode couldn’t be played. Please try again later.”


Firefox Browser –> Onscreen play error message: no error message displayed (the media just doesn’t play).

---

### Post by Holger_Gehrke on 2021-01-08
Tried to replicate your error on XUbuntu 18.04 using Firefox 84.0.1. Using your example 1 I got a list of episodes of the 'Hacks on Tap' podcast, chose the newest episode and got the same error. I then dug into the source code of the page using the 'Inspector' from Firefox's web-developer-tools, found an audio-element with an URL for an mp3-stream, cut-and-pasted that address into the address bar and had the podcast playing. I think it's some kind of JavaScripted stupidity which fails.
The same with example 3; didn't try the ones at apple.co since it should be the same content ...
Holger

---

### Post by tdog66 on 2021-01-08
Thanks, I appreciate you looking into this. I'm no expert on java implementation, but just to be sure, I checked my default settings in both Chrome and Firefox, and Javascript is indeed enabled. And when I checked the individual Google Podcast and Apple Podcast web pages, they correctly showed java enabled for the pages themselves as well (via "site settings"). If this were truly a javascript implementation issue, wouldn't it be strange to see it happening both in Chrome AND Firefox? 

I'm also wondering if by digging up the media source URLs and playing them directly, you might have somehow bypassed a possible codec issue (as wacky as that sounds). It's frustrating not having a better log file source to really track this down. Maybe others out there have additional ideas.

---

### Post by Holger_Gehrke on 2021-01-08
I don't think I could have bypassed a codec issue, because I opened the stream in a new tab in the browser. If the browser couldn't open the stream from the page, why should it be able to open it directly ? I really think it's something really stupid in the JS. The page is about **1.3 Megabyte**, almost all of that is Javascript.

Holger

---

### Post by tdog66 on 2021-01-11
Hi - since originally reporting this issue on Saturday, Jan 9, I was able to successfully replicate the errors several more times on Sunday, Jan 10th. 


However, when I attempted to do so again today (Jan 11), I found that all of the reported errors have now been corrected (i.e., I can now play the Google and Apple podcasts in my Chrome browser). 


Please note that I have not updated my Chrome version since the original report date, nor have I updated any Ubuntu Mate components (both of which are done manually, via the Linux terminal command line). I have also not rebooted my primary PC since the reporting date. 


Nonetheless, the errors appear to be no longer present at this time. And so I probably need to close out this bug report -- is there anything you need me to do on my end to accomplish this?


Many thanks for your timely help.

---

