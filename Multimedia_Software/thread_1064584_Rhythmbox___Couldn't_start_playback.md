---
title: "Rhythmbox   Couldn't start playback"
date: 2009-02-09
forum: Multimedia Software
---

### Post by zhanghuazhong on 2009-02-09
I created a new "Internet Radio Station"
[http://edition.cnn.com/audio/radio/winmedia.html](http://edition.cnn.com/audio/radio/winmedia.html)
But I get a warning "A text/html decoder plugin is required to play this stream, but not installed".  How can I get such plugin?

---

### Post by neu2buntu on 2009-02-11
heres your answer paste this into > rhythmbox > radio > new

```
mms://a1181.l3760631180.c37606.n.lm.akamaistream.net/D/1181/37606/v0001/reflector:31180
```im listening to your station now in rhythmbox

also noticed the station name shows up as none , but this is easy enough to edit just right click on "none" and choose properties and in basic ,change name....

---

### Post by zhanghuazhong on 2009-02-14
Thanks.But I have another problem,i cant change the name of the radio.Rhythmbox don't work if i try to change the name of CNN.

---

### Post by zhanghuazhong on 2009-02-14
I have solved it hehe

---

### Post by neu2buntu on 2009-02-15
glad you got it sorted,did my method work for you? as in the station url? and also changing the name from none? just to help anyone else on the forum....

---

### Post by zhanghuazhong on 2009-02-16
yes,I solved it with your method ,thanks,do you have more URLs,BBC,ABC and so on,thanks!

---

### Post by neu2buntu on 2009-02-17
here is bbc radio 1 live url ```
http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram
``` and abc has a few different stations so i will give u the url for this 1 ```
http://www.abc.net.au/streaming/RN.asx
``` if u want any more just post your request here!!!

---

### Post by zhanghuazhong on 2009-02-17
hehe&#65292;thanks!

---

### Post by neu2buntu on 2009-02-17
goto this thread "post #6" i have posted the method for getting the streams from a page 

[http://ubuntuforums.org/showthread.php?t=1071128](http://ubuntuforums.org/showthread.php?t=1071128)

now you can get all your fav stations on rhythmbox!!!!:-\"

---

### Post by zhanghuazhong on 2009-02-17
Great!I have tried your method, but how can you get CNN mms code,I goto CNN pages ,[http://edition.cnn.com/audio/radio/winmedia.html]("http://edition.cnn.com/audio/radio/winmedia.html") and I only got [http://edition.cnn.com/audio/radio/liveaudio.asx](http://edition.cnn.com/audio/radio/liveaudio.asx) and [http://i.a.cnn.net/cnn/.element/img/1.5/sect/cnnradio/64x112.speaker.swf](http://i.a.cnn.net/cnn/.element/img/1.5/sect/cnnradio/64x112.speaker.swf).

---

### Post by neu2buntu on 2009-02-18
the one ending in .asx plays in rhythmbox they dont have to be mms  also look for aac , m3u , xspf ,ram some streams dont even show a format...  if your rhythmbox doesnt play that stream then u will have to install the codecs for it   .. install "ubuntu-restricted-extras" make sure software sources has all repositories ticked on and in updates section choose "normal updates" .what i did was installed all gstreamer packages and audio lib files i could think of .

---

### Post by zhanghuazhong on 2009-02-19
all! Can i share?
I have a another question,I want to know some information of compiz plugins,and these fuction.
      I'm a Chinese,my english is not every well ,can i make friends with you ?
my skype ID is zhanghuazhong12
Thx!

---

### Post by boes on 2009-08-27
Hi neu2buntu, your steps are very simple but I still couldn't play this radio with rhythmbox. the site is [http://www.rnw.nl/id/bahasa-indonesia](http://www.rnw.nl/id/bahasa-indonesia) 
where the 'embeded' word is not in the media.
thank you

---

### Post by neu2buntu on 2009-08-28
> **boes said:**
> Hi neu2buntu, your steps are very simple but I still couldn't play this radio with rhythmbox. the site is [http://www.rnw.nl/id/bahasa-indonesia](http://www.rnw.nl/id/bahasa-indonesia) 
where the 'embeded' word is not in the media.
thank you

this site has an .html popup player ,which using the url wont work, but the on demand streams will work in rhythmbox, just goto the on demand stream you want and click on the mp3 icon and this will open up a new tab in firefox with the streams url,then just copy and paste it into rhythmbox.....   heres some i got for you to try ...

_[http://content70a.omroep.nl/8955f90addd811f3099185308150cf79/4a97f910/00/rnw/smac/en_bridgeswithafrica.mp3](http://content70a.omroep.nl/8955f90addd811f3099185308150cf79/4a97f910/00/rnw/smac/en_bridgeswithafrica.mp3)_



_[http://content70b.omroep.nl/f8499f495be0fa1718245501c176131b/4a97f972/03/rnw/smac/cms/eurohit40latest_2000_3000_44_1kHz.mp3](http://content70b.omroep.nl/f8499f495be0fa1718245501c176131b/4a97f972/03/rnw/smac/cms/eurohit40latest_2000_3000_44_1kHz.mp3)_



[http://content70a.omroep.nl/c6aef984311592fe6e4714fca4e94d0e/4a97f6d4/09/rnw/smac/cms/ejs2009promo_20090604_44_1kHz.mp3](http://content70a.omroep.nl/c6aef984311592fe6e4714fca4e94d0e/4a97f6d4/09/rnw/smac/cms/ejs2009promo_20090604_44_1kHz.mp3)


:guitar: i have noticed that the 1st 2 links wont open directly on here (ubuntuforums) but have tested in rhythmbox and they work ok..... just copy the links and paste into rhythmbox!!!

---

### Post by boes on 2009-08-28
those 3 links are not live program that I want to hear, they're kind of podcast files. the live program has the arrow symbol. when we click this arrow direct us to the current program. this is the actual problem which I couldn't listen to.
hope you can find the way and post it too and thanks for those links.

---

### Post by boes on 2009-08-28
this is what I've done: I uninstall all totems from Synaptic except libtotem-plparser12 and I go to that site and click the arrow and direct me to the Live Program and it works 100%. But I really don't know why by uninstalling all Totem the Live Program work?

---

