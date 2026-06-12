---
title: "Partial Lock w/ STB - No Programs being recorded anymore"
date: 2008-09-02
forum: Mythbuntu
---

### Post by hansoffate on 2008-09-02
I've had my STB working with mythbuntu for the past 6months flawlessly.  Just recently, I have been getting partial locks and now I can't record anything through the STB.

Any ideas on how to fix this?

Thanks,
Hans

---

### Post by hansoffate on 2008-09-07
Bump.  I've been fooling around with it by trying to change the data rate from 400 to 100, 200 and 800.  None of them seem to help.  This is killing me because now I can't record any HD programming.  Any help would be greatly appreciated.

Thanks,
Hans

---

### Post by newlinux on 2008-09-07
Are your recording via firewire from a STB? More info would help us help you. I'm assuming you are using firewire with a motorola or SA box? What model? Have you checked to see if your provider has changed the 5c status on the stations? 

or are you talking about RF passthrough to a QAM tuner from your STB?

---

### Post by hansoffate on 2008-09-08
> **newlinux said:**
> Are your recording via firewire from a STB? More info would help us help you. I'm assuming you are using firewire with a motorola or SA box? What model? Have you checked to see if your provider has changed the 5c status on the stations? 

or are you talking about RF passthrough to a QAM tuner from your STB?

I'm recording via firewire from a Motorola DCH-3200.  No, I haven't asked about 5c status.  What is 5c status?  I'll have to call comcast and ask.  

I pmed id about updating mythprime because I was having issues installing the new version.  I got it running and realized that my STB should have been set to p2p mode, so I changed that setting.  It is working about 75% of the time when changing channels.  Sometimes when changing to HD channels, it crashes and errors to the main screen that says the video can not be displayed.  Othertimes it stays on a black screen trying to display the video.  I noticed that htis happens mostly when it says "Partial Lock" instead of "LAM Lock".  Do you happen to know what these say?


Thanks,
Hans

---

### Post by newlinux on 2008-09-10
5C Is content protection used for firewire. It determines whether or not a non 5C device (such as a PC) can record the content. 5C setting can be different from channel to channel, and even program to program. You can check the 5c/CCI status of each channel on your motorola's service menu. I think there is a motorola wiki out there with explicit instructions. If not, if you google around you can find it. So first and foremost, I would check the settings on the stations you are having problems with. I think someone created a program called "scanfw" that will do these tests for you. Search the mythbuntu forums for it.

---

