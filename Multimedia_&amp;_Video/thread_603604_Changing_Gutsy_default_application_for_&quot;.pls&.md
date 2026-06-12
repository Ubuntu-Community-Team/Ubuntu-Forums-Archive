---
title: "Changing Gutsy default application for &quot;.pls&quot; streams"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by naniboujou on 2007-11-05
I want listen to an audio stream (mp3 format) from an Internet radio site. When I click the link, Firefox downloads what I assume is a JavaScript file ending with a ".pls" extension. This automatically opens Totem (no alternative option window appears) which is unable to play the stream. I have installed Audacious which I hope will do the trick but I need to know how to change the application default. There seem to be various MIME default links in several places in the file system and so far I haven't found the right one to work with. 

Also when I directly open a stored media file  ...say an ".mp3" ...   with a right click and specify an alternative application, how do I make that choice stick as a default? The 'open with' window seems to imply that the change SHOULD stick for all similar files -- just like it does in Windows -- but it certainly won't for me! (I am using Gutsy 7.10)

---

### Post by NilsE on 2007-11-05
On the first question you should go into the edit>preferences>content>manage file types and in the upper right corner of the window turn on mime types.  This may help you change the selection.  You may also want to install mplayer and the Totem/Mozilla plugins and see if that takes over and works.

On the second question right click on a file with the mime type you want and select properties.  There you will find a tab for "open with" where you can change the default program for that file type.

---

### Post by naniboujou on 2007-11-05
NilsE,

Thanks much!  On the first issue I must admit it didn´t even occur to me that this would be a Firefox preference. As for the second, I guess I must have stayed up way too late last night because your answer and some sleep have made it work. However, in my defense, if one right clicks, selects ¨Open with other¨ (rather than going to Properties)  the resulting window text IMPLIES that this change would be for all similar files. That is not the case, however. It is not even true for the same file opened again later. So I would be inclined to call the window text of that method some form of a ´bug´. 

Thanks again.

---

### Post by NilsE on 2007-11-05
> **naniboujou said:**
> NilsE,

Thanks much!  On the first issue I must admit it didn´t even occur to me that this would be a Firefox preference. As for the second, I guess I must have stayed up way too late last night because your answer and some sleep have made it work. However, in my defense, if one right clicks, selects ¨Open with other¨ (rather than going to Properties)  the resulting window text IMPLIES that this change would be for all similar files. That is not the case, however. It is not even true for the same file opened again later. So I would be inclined to call the window text of that method some form of a ´bug´. 

Thanks again.

I hear ya.

I just always assumed that the drop down open with option was one time and the preference option was forever.  

I kind of like it the way it is. For example I can do a quick view of a .png file with the default viewer and edit it with Gimp with the pop up open with option. Really comes down to user preference.

---

### Post by naniboujou on 2007-11-05
Yes, I think it does make sense in the way it works -- one should have both options. It´s the window text that is misleading.

---

