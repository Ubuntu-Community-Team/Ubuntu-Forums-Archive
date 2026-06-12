---
title: "cmi8738, can't record, have possible fix but can't implement"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by takayuki on 2008-03-18
Hi,

i've got a cmi8738 based sound card.  i installed the drivers from the alsa site and the sound works, but i can't record (no skype!).  i found the solution below, but don't have an asound.state file to work with...  any thoughts?


> If you can’t record using a microphone on the CMI8738 card under Linux… For the 3 people in the universe who have my exact same problem, that is, they can’t record audio using a microphone on the CMI8738 card under Linux… here’s the solution: To enable the microphone on the 0.9 series: 

1. run “alsactl store” 
2. 2. edit /etc/asound.state. Set “Mic As Center/LFE” to “false”. 
3. 3. run “alsactl restore” 
4. If your Mic is set to “Record” and capture level is appropriately high, the Mic should now work.

 (My thanks to Lukasz Weber for pointing this out.) There is also a friendly way: kmix allows you to set the “Mic As Center/LFE” property to “false” using the GUI.

thanks,

takayuki

---

