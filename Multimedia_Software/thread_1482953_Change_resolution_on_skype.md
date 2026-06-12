---
title: "Change resolution on skype?"
date: 2010-05-14
forum: Multimedia Software
---

### Post by P-rench on 2010-05-14
How do I change the resolution in skype 2.1 beta on ubuntu 9.10?? At the moment my webcams resolution appears to be half the size of what it should be which is creating a double vision/image of me and I can only see about half of my head vertically. My resolution should be 640X480, but it clearly is not. It looks way smaller like 320X240 . How do I fix this? :confused:

---

### Post by P-rench on 2010-05-14
I found this command that is supposed to change the resolution on skype, but it didn't work. Why?? This was the command 

On Linux: 

go to: 

/$HOME/.Skype/(YourUserName)/config.xml 

search for the Video tag and modify there your parameters, as: 


<Video> 
   <CaptureHeight>480</CaptureHeight> 
   <CaptureWidth>640</CaptureWidth> 
</Video> 

When I typed in the first command - "/$HOME/.Skype/(YourUserName)/config.xml"  I got this error - "ghost@ubuntu:~$ /$HOME/.Skype/phrench17/config.xml 
bash: //home/ghost/.Skype/phrench17/config.xml: Permission denied" 
 
I can't seem to find the skype directory folder and I can't seem to find config.xml? What is config.xml? Why isn't this command working? I just want to change the resolution on skype to the correct resolution of my webcam which is 640X480! Please Help!!?? :confused:

---

### Post by xc3RnbFO8P on 2010-05-14
Try:
> gedit /$HOME/.Skype/phrench17/config.xml 

---

### Post by P-rench on 2010-05-14
Ok, Thanks Ringi! The command did work finally, but I wasn't able to find any "video" section. This is basically the section that I narrowed it down to after I did the command. The rest of the xml was completely unrelated to video, resolution, and webcam as far as I could see, except for possibly this part.  

<AnimateEmoticons>0</AnimateEmoticons>
    <AutoPopupChatWindow>1</AutoPopupChatWindow>
    <CaptureDevice>PulseAudio server</CaptureDevice>
    <LastSendPath>/home/ghost/Downloads</LastSendPath>
    <RingDevice>PulseAudio server</RingDevice>
    <SoundDevice>PulseAudio server</SoundDevice>
    <TransferWindow>
      <Height>240</Height>
      <NoCancelConfirmation>0</NoCancelConfirmation>
      <Width>480</Width>
      <X>3</X>
      <Y>647</Y>
    </TransferWindow>
    </UI>
</config> 

Is "capture device" supposed to be the webcam? Is "transfer window" the resolution of the webcam? I did try fiddling around with the transfer window's height and width, I even added a "video" part as previously seen in this thread, but still nothing. The webcam is still putting out a messed up picture. Maybe I should restart my computer after applying changes? Still need help. Advice and suggestions?? I'm stuck :confused:

---

### Post by xc3RnbFO8P on 2010-05-14
I have never try it, but I would try:
> <Height>**480**</Height>
<NoCancelConfirmation>0</NoCancelConfirmation>
<Width>**640**</Width>

---

### Post by P-rench on 2010-05-14
Alright, just tried that and restarted ubuntu, then I did a "video test" in skype and my webcam still doesn't work right, nothing has changed. Thanks for the suggestion though. Still confused, any more suggestions and help??? :confused:

---

### Post by xc3RnbFO8P on 2010-05-14
Try to change this:
> <TransferWindow>
<Height>240</Height>
<NoCancelConfirmation>0</NoCancelConfirmation>
<Width>480</Width>
<X>3</X>
<Y>647</Y>
</TransferWindow>
to:
> <Video>
<CaptureHeight>480</CaptureHeight>
<CaptureWidth>640</CaptureWidth>
</Video> 

---

### Post by P-rench on 2010-05-14
Ok I tried that, and still nothing. Does it matter how it's lined up in the xml file? Does it have to be a certain way? I don't understand why this webcam won't work right! Skype is detecting the webcam and there is an image when I hit the "test" button in skype, but the image is still all messed up. Thanks for the suggestion though! Anyone else have anymore suggestions or answers? I could really use them right now as I'm not really sure what to do at the moment. :confused:  

P.S. This might be worth mentioning as well, when I open up gstreamer-properties in a terminal my webcam is not detected, no matter what I do, it just will not work in gstreamer at all, no image or anything. So I dunno whats up with that.

---

### Post by P-rench on 2010-05-14
YES! IT'S SOLVED! Thanks to Ringi and user no2498 where I found part of the solution in their reply to this thread [http://ubuntuforums.org/showthread.php?t=1482369](http://ubuntuforums.org/showthread.php?t=1482369).  Alright so my webcam is now working in Skype 2.1 Beta Version on Ubuntu 9.10!!! I want to mention that this solve is for a SiGma Micro USB Webcam ID# 1c4f:3002. This webcam is EXTREMELY cheap (about $7 after shipping) and works GREAT! The only downside is, there is no built in microphone. If anyone here is interested in purchasing the same webcam I bought, you can do so at [http://www.amazon.com/Webcam-Camera-Vision-Meeting-compatible/dp/B0015TJNEY/ref=sr_1_1?ie=UTF8&s=electronics&qid=1273875133&sr=8-1](http://www.amazon.com/Webcam-Camera-Vision-Meeting-compatible/dp/B0015TJNEY/ref=sr_1_1?ie=UTF8&s=electronics&qid=1273875133&sr=8-1) through the seller "HDE". OR, you can buy directly from HDE at their home website here [http://www.hdeshop.com/USB-3-LED-PC-Webcam-Camera/M/B0015TJNEY.htm](http://www.hdeshop.com/USB-3-LED-PC-Webcam-Camera/M/B0015TJNEY.htm) This webcam is very much worth the price and purchase, very decent quality at a resolution of 640X480 and very little or no lag between voice and video when chatting it up on skype! =] Ok, now to the answer! I did all of this in the terminal and everything worked great.

                                 First you will want to set the resolution for skype to the same resolution of the webcam. Before doing this, Shut down Skype and any other video/webcam program before doing anything. Then open a terminal. To do this, go to Applications menu -> Accessories -> Terminal.   
  
Now enter this command in the terminal: 
 
gedit /$HOME/.Skype/(YourUserName)/config.xml   
 
Once the skype xml file is opened then search for this:  
 
<TransferWindow>
<Height>240</Height>
<NoCancelConfirmation>0</NoCancelConfirmation>
<Width>480</Width>
<X>3</X>
<Y>647</Y>
</TransferWindow>   
 
Once found, highlight and delete, and replace with this:  
 
<Video>
<CaptureHeight>480</CaptureHeight>
<CaptureWidth>640</CaptureWidth>
</Video>    
 
Once completed, save and exit. Now return to the terminal.  
 Now you will need the webcam drivers so enter these commands in the terminal (one by one):

cd /tmp
wget [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)
tar xvfj tip.tar.bz2
cd v4l*
make
Wait, until it is finished (it will finish with an error).

Now, enter this in the terminal:

gksudo gedit /tmp/v4l*/v4l/.config

Search for this line in the xml file:
CONFIG_DVB_FIREDTV=m 

and change it to
CONFIG_DVB_FIREDTV=n 

Now click on "Save", close the text editor and get back to the terminal where you enter these commands (one by one):

make
sudo make install

Now, when completed, reboot your computer and your webcam should work.   

Enjoy! =]

---

