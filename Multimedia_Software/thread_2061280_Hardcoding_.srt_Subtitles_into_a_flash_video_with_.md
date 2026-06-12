---
title: "Hardcoding .srt Subtitles into a flash video with Menplayer"
date: 2012-09-22
forum: Multimedia Software
---

### Post by hislordship on 2012-09-22
Hallo:-) I have downloaded a movie off Youtube in the .flv video format and want to hardcode subtiltes into it. I don't understand much about video editing so I've been searching for someone to give me the magic words to enter into the terminal in order to achieve this. The subtitles are already done using gnome-subtitles and saved in the .srt format.

I would like the subtitles to be displayed in a well readable color, such as neon green and at the TOP of the screen because there are subs encoded at the bottom in a different language already. I want to burn the video with the subtitles to a DVD that can be played  with no problems on a DVD player in Europe (PAL)

Any geek here who can help me please??

---

### Post by hislordship on 2012-09-22
I managed to put well readable subtitles at the top of the page using these commands in mencoder. There was an error message that the aspect wasn't defined, but it didn't seem to matter.


  	 	 	 	 	 	   mencoder ./Desktop/oldmoviewithnosubsflv -o newmoviewithsubs.mp4 -sub ./Desktop/mysubtitlefiler.ssa -ovc lavc -oac faac -subpos 15

---

