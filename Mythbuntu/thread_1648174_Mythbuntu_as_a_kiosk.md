---
title: "Mythbuntu as a kiosk"
date: 2010-12-18
forum: Mythbuntu
---

### Post by USSEnterprise on 2010-12-18
Hello.

Let me preface this post by saying that, while I have dabbled with Linux on and off for several years, I am still a relative newbie.

I run a small exhibit at a museum about the history of (and in the theme of) fallout shelters and the Cold War. The exhibit is located within a space that was formerly a fallout shelter. I am trying to set the exhibit up so that it is somewhat self-sustaining, in that a person does not need to be present to give a tour. Basically, I am trying to set up mythbuntu with several videos, some that I make as a virtual tourguide, and some of the old Public Service Announcements and propaganda films. I basically need to accomplish two things:

1, Lock down functionality of the software so people visiting can't screw with it.

2. Be able to play videos by pressing a single key on the keyboard (i.e. pressing the "a" key plays "duck and cover.mpg"

Thanks for any help you can provide. I really appreciate it!

Joe

---

### Post by thatguruguy on 2010-12-18
It strikes me that setting up mythbuntu for this functionality would be overkill, unless you really need to be able to occasionally stream live tv on the kiosk.

Who is going to have access to the keyboard?  If the general public has access to a full keyboard attached to your system, I'm not sure how you would set it up so that "people visiting can't screw with it."

If I were setting something up like you're describing, I think I'd set it up as a web page with the browser set to full screen and the video set up to run in a div. Then, I'd write a script to poll the keyboard, and only provide a numpad to the public to use. Of course, that would only allow as many videos as there are keys on the numpad, but you didn't state how many videos you want to host.

---

### Post by USSEnterprise on 2010-12-20
I'm not much of a programmer, even simple HTML. That's why I was thinking of using mythbuntu. Keyboard access will limited to a few select keys via a keyboard encoder for use with a MAME arcade setup.

---

### Post by thatguruguy on 2010-12-20
Assuming that your user name is jamestkirk, and you have videos named foo1.avi, foo2.avi (etc.) in your /home/jamestkirk/Videos directory, the following would create a web page that would allow you to select from 9 videos by pressing keys 1-9:
```
<html>
<head>
<script language="javascript">
var myVids=new Array("","foo1.avi","foo2.avi","foo3.avi","foo4.avi","foo5.avi","foo6.avi","foo7.avi","foo8.avi","foo9.avi")
var menulist="<br><br>Please select from the following:<br><br>&nbsp;1. foo1<br>&nbsp;2. foo2<br>&nbsp;3. foo3<br>&nbsp;4. foo4<br>&nbsp;5. foo5<br>&nbsp;6. foo6<br>&nbsp;7. foo7<br>&nbsp;8. foo8<br>&nbsp;9. foo9";
var pressedkey;
function showvid(e){
pressedkey=parseInt(String.fromCharCode(e.which));
if(pressedkey >= 1 && pressedkey <=9){
document.getElementById("viddiv").innerHTML = '<EMBED src="/home/jamestkirk/Videos/'+myVids[pressedkey]+'" width=100% height=100% type=video loop="false" repeat="false" autostart="true">';
}
else{
showMainMenu();
}
}
function showMainMenu(){
document.getElementById("viddiv").innerHTML =menulist;
}
</script>
</head>
<body bgcolor="black" onload="showMainMenu()" onkeypress="showvid(event)" id="pagebody">
<br><br>
<div name="viddiv" id="viddiv" style="width:100%;height:800px;align=center;color:white;font:20px bold arial,helvetica,sans-serif;">
<!-- the following is just a place holder -->
&nbsp;
</div>
&nbsp;
</body>
</html>

```

---

