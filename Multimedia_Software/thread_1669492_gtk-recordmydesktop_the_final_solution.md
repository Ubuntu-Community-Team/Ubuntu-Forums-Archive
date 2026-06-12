---
title: "gtk-recordmydesktop the final solution"
date: 2011-01-17
forum: Multimedia Software
---

### Post by shalkam on 2011-01-17
Hi,
I have been around for like 2 weeks of more trying to get gtk-recordmydesktop to work and finally I have managed to figure out the solution and I will share it here in this post

[B]this post includes solution for the following problems
[/B]
[LIST]
[*] video moving too fast - frame skipping - audio video out of sync ex. [http://www.youtube.com/watch?v=JezEOS_V1JI](http://www.youtube.com/watch?v=JezEOS_V1JI)
[*] video of low quality - image all missed up
[/LIST]

[LIST]
[*] sound issues
[/LIST]

[B]settings that worked for me
[/B]
[LIST]
[*]sound and video quality both 100%
[/LIST]
     _performance(image attached_

[LIST]
[*]frames per second 15
[*]encode on the fly -> disabled
[*]zero compression -> enabled
[*]quick subsampling -> disabled
[*]full shots at every frame -> enabled
[/LIST]
      [U]audio (image attached)
[/U]
[LIST]
[*]channels : 1
[*]freq. : 48000
[*]device : default "lower case"
[/LIST]

then I used the following post for fixing the sound [http://ubuntuforums.org/showthread.php?t=1584849&page=1](http://ubuntuforums.org/showthread.php?t=1584849&page=1)

type  "pavucontrol" in terminal to launch pavucontrol

when using this sound fix I need you to notice two things
1- the input devices tab, at the bottom you can choose which input devices to be monitored (image attached )
2- the recording tab, there you can find "alsa plugin [recordmydesktop]" and there will be two options switch between the two to record computer sound or from the mic (image attached )

[COLOR=Red]_**the last and the most important point is not to press the record button directly YOU MUST  select an area to be recorded from the mini-desktop in the gtk-recordmydesktop window ( last image )**_[/COLOR]

I have uploaded a video to youtube with the instructions but it is in arabic 
just in case you want to see the above instructions in action [http://www.youtube.com/watch?v=5__sJkbeDvE](http://www.youtube.com/watch?v=5__sJkbeDvE)

regards,
Mostafa

---

