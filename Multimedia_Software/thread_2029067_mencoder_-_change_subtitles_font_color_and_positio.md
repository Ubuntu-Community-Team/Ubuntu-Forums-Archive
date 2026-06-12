---
title: "mencoder - change subtitles font color and position"
date: 2012-07-19
forum: Multimedia Software
---

### Post by bloodstreetboy on 2012-07-19
I am using mencoder on command line (terminal) to add subtitles on video.
I am using .srt file for subtitles. I want to change font color of subtitles. It shows always white.
If color change is not possible using srt files, please tell me how to make black font color of subtitles. May be if white is possible from .srt files, then black should be possible.
If color change is not possible from .srt files,please tell me syntax for .saa or .a$$ files. Tell me the styles what should I add in text editor for .a$$ files
If I want to print these three lines in corners(top-left, top-right, bottom-left or bottom-right) of video, how can it be possible?Using -subpos, subtitles move vertically and remains center of the video. I want to move them horizontally.
The three lines are phone numbers:-
111-222-3333
444-555-6666
777-888-9999
It should be appeared like this on corners of the video.
I am using following command to print subtitles.
```
mencoder "/media/sda6/filename.avi" -oac copy -ovc lavc -sub "/media/sda6/subtitles.srt" -utf8 -subfont-text-scale 5 -font 'Bitstream Vera Sans:style=Bold' -o "/media/sda6/output.avi"
```Please do not suggest about drawtextfilter. It is not enabled on my system. I have done everything to enable it and it is not done yet.
Please help.

---

### Post by pavi_elex on 2012-07-20
I do not know it using mencoder but I can solve your one problem out of two.
I can put colored text on video using software avidemux.
I do not know about your other requirement that is position of text.
May be you want to do this using only mencoder but take a look.

```
1. Download avidemux from  software center.
2. Open your video in it.
3. Select Video, Audio and format in left hand side bar. Change "copy" from audio and video & select your desired codec. If you don't change copy, u can't do step-4.
4. Now, Video -> Filters -> subtitles -> subtitler -> click on + sign
5. Select subtitle file, Select ttf font file, Encoding UTF-8, Select font color, Select size and position of your text. Click ok & close filter box.
6. Now , File -> save -> save video -> save
```

You will be able to see text in color. You can move text vertically but can not move it horizontally. As you have written, you can move text vertically by mencoder too but can not place it at corners. Through this method, you can not place at corners.
May be some one will give you the right solution using mencoder.

---

### Post by pavi_elex on 2012-07-23
I have a temporary solution for position. It is not like fix a position of text using attributes like -subpos or -subwidth. That is why I am saying it is temporary solution.

Open your srt file and move the position of text using spacebar.
Example :-if you want to print text in bottom right side.
```
00:01:20,001 --> 00:01:26,000 
                                                     888-909-5151 
                                                     818-765-8000 
                                                     310-385-7979
```if you want to print text in bottom left side.
```
00:01:20,001 --> 00:01:26,000 
888-909-5151                                                      
818-765-8000                                                      
310-385-7979                                                    
```There is long space after text in each line.

You can adjust spaces after text according to your desired horizontal position.
And You said you can print text vertically.
Now combination of both you can print text any where on video.
I hope, you have understood my point.

---

### Post by bloodstreetboy on 2012-07-24
Thanks for your both solutions. As I said I want to do it using mencoder or command line. I do not want to use any software. Sorry I couldn't try Avidemux but it looks good solution for emergency.
But your temporary solution is perfect and right now it is permanent for me. I have used it in mencoder and it is working flawless.
I was able to move text vertically at center of the video using attribute -subpos before. But it is very good solution if I set position of text using spaces in srt file, that's why I can put text anywhere on video.

Please find solution of color text problem using mencoder or command line. You have solved my 50% problem.
Thank you once again.

---

### Post by qyot27 on 2012-07-24
> **bloodstreetboy said:**
> I am using mencoder on command line (terminal) to add subtitles on video.
I am using .srt file for subtitles. I want to change font color of subtitles. It shows always white.
If color change is not possible using srt files, please tell me how to make black font color of subtitles. May be if white is possible from .srt files, then black should be possible.
SRT can use HTML formatting.
```
0
00:00:00,000 --> 00:00:05,000
<font face="Ubuntu Light" color="black">Hello, how are you?</font>

```
Will render the text as black in the 'Ubuntu Light' font, or it *should*.  Whether the player supports it is another matter entirely.

> If color change is not possible from .srt files,please tell me syntax for .saa or .a$$ files. Tell me the styles what should I add in text editor for .a$$ files
The syntax needed for [color="black"]A[/color]SS is much more complex*, and really the best option for making sure they look exactly how you want them to look is to use Aegisub to make sure the styling, positioning, and timecodes are correct and the styles applied to the precise lines correctly.  Joining them to the video can then be done on CLI, but the styling itself is better left to a solution that can show immediate results.

*an [color="black"]A[/color]SS equivalent of the SRT example from above (with some of Aegisub's metadata):
```
[Script Info]
; Script generated by Aegisub 2.1.9
; http://www.aegisub.org/
Title: Default Aegisub file
ScriptType: v4.00+
WrapStyle: 0
PlayResX: 848
PlayResY: 480
ScaledBorderAndShadow: yes
Collisions: Normal
Video Aspect Ratio: 0
Video Zoom: 6
Video Position: 0
Last Style Storage: Default

[V4+ Styles]
Format: Name, Fontname, Fontsize, PrimaryColour, SecondaryColour, OutlineColour, BackColour, Bold, Italic, Underline, StrikeOut, ScaleX, ScaleY, Spacing, Angle, BorderStyle, Outline, Shadow, Alignment, MarginL, MarginR, MarginV, Encoding
Style: Default,Ubuntu Light,20,&H00000000,&H000000FF,&H00000000,&H00000000,0,0,0,0,100,100,0,0,1,2,2,2,10,10,10,1

[Events]
Format: Layer, Start, End, Style, Name, MarginL, MarginR, MarginV, Effect, Text
Dialogue: 0,0:00:00.00,0:00:05.00,Default,,0000,0000,0000,,Hello, how are you?
```





Personally, I stopped using mencoder for most quick transcoding things quite a while ago.  If I need to hardcode subtitles, I use the encoding branch of mplayer2 (and then ffmpeg to mux the video and audio back together).

---

