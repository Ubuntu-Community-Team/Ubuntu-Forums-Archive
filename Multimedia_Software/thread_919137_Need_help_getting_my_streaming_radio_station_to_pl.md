---
title: "Need help getting my streaming radio station to play"
date: 2008-09-13
forum: Multimedia Software
---

### Post by gen1mx6 on 2008-09-13
[http://www.wsccfm.com/main.html](http://www.wsccfm.com/main.html) is the main page i click the listen live link(its near the top right in the on air box) and the advertisement plays audio but i don't hear the stream, i have java script enabled on firefox and don't know what else i can do thank you for your help

(my version of ubuntu i got from Wubi so the newest hardy version)

---

### Post by Atsuko on 2008-09-13
Don't think it will play.. 
> Click Here To Install Your ActiveX Plug-In
Uses ActiveX.

---

### Post by markbuntu on 2008-09-14
OK, you can get it. On the front page click on the HD radio icon. On the next page click on the stream you want to listen to. On the popup window right click and choose page source. Scroll down that until you see this line:

<PARAM NAME="FileName" VALUE="http://mfile.akamai.com/49395/live/reflector:35127.asx?bkup=35612">

copy from the "http//......." into the Rythmbox/Music/New Internet Radio Station box. Leave out the quotation marks.

That works for me. I am listening to it right now.

No need for windows, or ActiveX plugins, etc.

You can do this for pretty much any radio station. Just look in the source for the "http://.......asx" and copy it into your internet radio player.

---

### Post by gen1mx6 on 2008-09-16
ok, the hd radio channel doesn't give me the 94.3 talk radio it gives me 94.3 jazz :( the thing is i can actually hear this music directly from the popup window just can't hear the original one lool

---

