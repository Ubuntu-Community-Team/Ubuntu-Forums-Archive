---
title: "Video recording on Facebook."
date: 2009-01-28
forum: Multimedia Software
---

### Post by zeelex on 2009-01-28
For some reason I am unable to post videos to my friend's facebook pages. By post, I mean I am unable to record a video directly through Facebook onto his/her page. I imagine this is an issue with Adobe Flash Player. Does this problem apply to anyone else?



The webcam light does not turn on and the prompt remains as follows,
 
[IMG]http://img240.imageshack.us/img240/5408/issuelf0.jpg[/IMG]


Anyone information on how to resolve this issue would be greatly appreciated, Thank you.

---

### Post by Major_Rager on 2009-02-06
I am experiencing the exact same problem and it's peeving me off!:(

---

### Post by UbuntuNerd on 2009-02-06
I think it might work with "java" and you may not have it install. if that is the case type this in a terminal: 
```
sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin
```
Oh crap I miss read your question I thought you meant the photo uploader for some reason my bad I need to go to bed been up to long.

---

### Post by zeelex on 2009-02-09
Am I only the only person using Facebook and Ubuntu, noone else is having this issue?

---

### Post by loell on 2009-02-09
maybe your webcam isn't recognized.

---

### Post by binbash on 2009-02-09
bump, i have same issue

---

### Post by zeelex on 2009-02-10
It works fine in programs like Ekiba and Skype, as well as Cheese and Camorama. I don't think it has to do with Video 4 Linux.

---

### Post by Stillmatic on 2009-03-06
bump! I have the same issue w/ flash not recognizing my webcam on my ubuntu mi laptop!

---

### Post by Janoma on 2009-03-21
It must be some error in Facebook. I have exactly the same problem, though the webcam works ok in youtube, for example.

---

### Post by benhur99ph on 2009-03-22
I too have the same problem. I think its a matter with facebook. Because I tried using TokBox -- a video conferencing website that also uses your webcam through adobe's flash player -- and it works fine. With facebook, it just sit there (your screenshot) forever.

---

### Post by stukpixel on 2009-06-22
bump.

same issue here.

---

### Post by lokster on 2009-06-28
I have the same issue with Ubuntu 9.04

---

### Post by kevindubrow on 2009-08-01
I have this same problem on my HP Mini. Has anyone figured this out?

---

### Post by neoforest on 2009-08-09
Having same problem here on Ubuntu 9.04

---

### Post by timcredible on 2009-08-14
yep, i just bought a webcam, works in skype and cheese, but facebook just sits there.  using 9.04

---

### Post by davidmerrick on 2009-08-15
Yep definitely same issue here. Flash works on most everything except for recording video on Facebook. I'm using 9.04 as well.

---

### Post by jeffreypine on 2010-07-12
bump.

same issue here.

Ubuntu Lucid 10.04

---

### Post by gausie on 2010-10-28
I'm also experiencing this problem... although it doesn't seem anyone knows anything about it!

---

### Post by gausie on 2010-10-28
I've managed to fix it for me. I'll show you what I did (it's fairly simple).

[LIST]
[*]Opened the SWF (Flash file) in a separate window (for me it was [http://www.facebook.com/rsrc.php/zK/r/N6nsZA_xMj8.swf](http://www.facebook.com/rsrc.php/zK/r/N6nsZA_xMj8.swf). If that doesn't work, find it with a DOM inspector)
[*]It will ask if Facebook is permitted to use your webcam. Click "Yes" and "Remember answer".
[*]Close the window with the SWF and reload your Facebook window.
[*]Try to record a video again, and it should work!
[/LIST]

Gausie

\\:D/

---

### Post by no2498 on 2010-10-28
you can set that in the adobe settings manager
at the adobe site

---

### Post by tmray on 2010-11-24
> **gausie said:**
> I've managed to fix it for me. I'll show you what I did (it's fairly simple).

[LIST]
[*]Opened the SWF (Flash file) in a separate window (for me it was [http://www.facebook.com/rsrc.php/zK/r/N6nsZA_xMj8.swf](http://www.facebook.com/rsrc.php/zK/r/N6nsZA_xMj8.swf). If that doesn't work, find it with a DOM inspector)
[*]It will ask if Facebook is permitted to use your webcam. Click "Yes" and "Remember answer".
[*]Close the window with the SWF and reload your Facebook window.
[*]Try to record a video again, and it should work!
[/LIST]

Gausie

\\:D/
Finally! Been trying to fix this forever. Thanks

---

### Post by blueberrywoo on 2011-02-23
Fixed it 1 minute ago:

1. Go to [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager03.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager03.html)
2. Go to Global Security Settings and select "Always allow" (if you want to allow ALL websites who require webcam to be allowed to use yours)
3. Go to Website Privacy Settings and click on the websites given bellow that already wanted to use your webcam, select "Always allow"

---

