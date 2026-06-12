---
title: "How to get 16:9 720x480 SD to display as 853x480."
date: 2012-06-06
forum: Mythbuntu
---

### Post by topcat5 on 2012-06-06
One of the local TV stations transmits one of its SD signals (MeTV) as an anamorphic 16:9 aspect ratio with a resolution of 720X480.  It's 480i. The TV station adds the bars to the side.   Thus on a wide screen TV that is actually received by the TV the resulting picture is 853x480 on a 16x9 display with bars filling the remaining space.  The TV must be set to 16x9 on this channel to properly display this picture.   

However when MythTV gets this signal, it decides to repackage it and I end up with a 720X480 with wider side bars.  It's not as easy to watch as I end up with a smaller picture and the aspect seems a little "off". 

My question is what settings do I change to get Myth to simply pass the original 853x480 format to the TV?   

I hope this request is clear enough as it's taken me several days of reading about aspect ratios, etc just to gain enough knowledge of what is going on to even ask this question.   Thanks in advance.

---

### Post by tgm4883 on 2012-06-06
> **topcat5 said:**
> One of the local TV stations transmits one of its SD signals (MeTV) as an anamorphic 16:9 aspect ratio with a resolution of 720X480.  It's 480i. The TV station adds the bars to the side.   Thus on a wide screen TV that is actually received by the TV the resulting picture is 853x480 on a 16x9 display with bars filling the remaining space.  The TV must be set to 16x9 on this channel to properly display this picture.   

However when MythTV gets this signal, it decides to repackage it and I end up with a 720X480 with wider side bars.  It's not as easy to watch as I end up with a smaller picture and the aspect seems a little "off". 

My question is what settings do I change to get Myth to simply pass the original 853x480 format to the TV?   

I hope this request is clear enough as it's taken me several days of reading about aspect ratios, etc just to gain enough knowledge of what is going on to even ask this question.   Thanks in advance.

Is this a digital or analog signal? I'm guessing it's digital since you are saying this one channel broadcasts at a different resolution. If this is the case, then MythTV isn't altering what it is recordings (digital recordings just get written to the disk as they are already encoded).

To fix your issue, we'll need a bit more info. For instance, you say it's 480i, but I don't think that means what you think it means. Do you mean to say that the picture is 4:3 rather than 16:9, yet the TV station adds black bars on each side so the signal is a 16:9 transmission?

---

### Post by anonymousdog on 2012-06-06
> **tgm4883 said:**
> ...I don't think that means what you think it means.
Awesome Princess Bride reference (even if unintended)!:lolflag:

---

### Post by topcat5 on 2012-06-06
This is ATSC video in the USA.  It's a sub-channel that is transmitted as standard definition.  I don't think MythTV is altering what is being transmitted in regards to receiving the signal and storing it on the disk, but the internal player is indeed displaying the picture at a different aspect ratio and resolution than how it's displayed natively on the TV.  

If this were a 4:3 discussion only, then then commonly, the TV stations will send either a 640x480, 704x480  and sometimes 720x480 resolution signal.  640x480 is the only native 4:3 format.  The other two resolutions will get modified to an aspect ratio of 4:3. For this reason you don't often see 720x480 being sent by TV stations because it's a waste of bandwidth.  

However in this case the station is sending a 720x480 resolution picture as part of a 16:9 anamorphic picture including the sidebars.   The ATSC receiver then displays the video on a wide screen as a 853x480 resolution display.  This allows the TV station so send a slightly enhanced picture if viewed on a widescreen TV.   

So when I watch this station with the TV connected directly to an antenna, I see a 853x480 picture.  It's wider and the aspect ration is 16:9.  But when I display this channel through MythTV's player, it does not just pass the video unchanged.   For some reason it's attempting to down convert the video back to 4:3 resolution so I end up looking a a narrower picture with larger sidebars.  I suspect it's looking at the data stream 720x480@29.97 and choosing a default 4:3 for it.  

So what I'm looking for are the settings in MythTV, that stop the internal player from doing this.

---

### Post by matt06 on 2012-06-06
Have you looked at the TV Playback settings?  It's been a while since I've dug around in there, but I do recall a AutoZoom or Auto-Fill setting.  I set mine to OFF instead of Auto and ended up just mapping a button on my remote to adjust fill when I needed to change it.

---

### Post by nickrout on 2012-06-07
> **topcat5 said:**
> This is ATSC video in the USA.  It's a sub-channel that is transmitted as standard definition.  I don't think MythTV is altering what is being transmitted in regards to receiving the signal and storing it on the disk, but the internal player is indeed displaying the picture at a different aspect ratio and resolution than how it's displayed natively on the TV.  

If this were a 4:3 discussion only, then then commonly, the TV stations will send either a 640x480, 704x480  and sometimes 720x480 resolution signal.  640x480 is the only native 4:3 format.  The other two resolutions will get modified to an aspect ratio of 4:3. For this reason you don't often see 720x480 being sent by TV stations because it's a waste of bandwidth.  

However in this case the station is sending a 720x480 resolution picture as part of a 16:9 anamorphic picture including the sidebars.   The ATSC receiver then displays the video on a wide screen as a 853x480 resolution display.  This allows the TV station so send a slightly enhanced picture if viewed on a widescreen TV.   

So when I watch this station with the TV connected directly to an antenna, I see a 853x480 picture.  It's wider and the aspect ration is 16:9.  But when I display this channel through MythTV's player, it does not just pass the video unchanged.   For some reason it's attempting to down convert the video back to 4:3 resolution so I end up looking a a narrower picture with larger sidebars.  I suspect it's looking at the data stream 720x480@29.97 and choosing a default 4:3 for it.  

So what I'm looking for are the settings in MythTV, that stop the internal player from doing this.

Perhaps you should upload a sample somewhere, might be easier for people to understand your situation and suggest a solution.

I assume you have used the zoom options (mapped to w by default I think) ? can also be accessed via the menu button (M key) during playback.

---

### Post by topcat5 on 2012-06-07
Yes, I've tried to use zoom, manually changing the aspect ratio, etc.   I'm not sure how I would take a screenshot of my TV receiving the station by it's native receiver.   

Another way to think about it would be to imagine that it is a 16:9 transmission, with a 720 x 480 video in the center.  Since the video is also a 480i transmission (instead of 720P or 1080i) the TV sets the vertical size to 480 and you end up with a video that is 853 wide.  (the rest being side bars)   

Myth unfortunately sees that it is a 720x480 video (or maybe it triggers off the 480i) so tries to scale the picture like it was 4:3 display. The result is a picture that is 480 high by 720 (instead of 853) which is inferor since it looks a bit squished.     

It's not an often noticed problem since I assume there are not many people who have a TV directly connected to an Antenna and also have a local station that transmits a SD channel in this manner.

---

### Post by nickrout on 2012-06-07
I am not asking for a screenshot. I am asking for a sample of the file. Please upload one somewhere, like dropbox, (megaupload LOL?).

30 seconds would do, easiest way would be to record livetv on that channel for 30 sec and then exit livetv and upload the resulting file.

Or take an existing recording and use command line tools to cut a piece out, the beauty of mpeg-ts files is that you can cut a chunk out anywhere.

---

### Post by topcat5 on 2012-06-07
> **nickrout said:**
> I am not asking for a screenshot. I am asking for a sample of the file. 

OK, here is a sample recording.   

[http://sharesend.com/n7an9]("http://sharesend.com/n7an9")

---

### Post by nickrout on 2012-06-07
> **topcat5 said:**
> OK, here is a sample recording.   

[http://sharesend.com/n7an9]("http://sharesend.com/n7an9")

I'll take a look tomorrow :)

---

### Post by topcat5 on 2012-06-07
I just realized that I explained this incorrectly.  I've done a crash course on aspect ratios in the last couple of days and don't do justice to what seems to be an amazingly complex subject.   I'll take another stab at it to try and to be more clear.  

There are 3 formats commonly sent by TV stations, 1080i, 720p and 480i.  There are also 2 common aspect ratios 16:9 & 4:3.  From what I can see the following assumptions are made.  1080i & 720p are 16:9 and 480i could be either.   

When a TV sees these formats it will effectively set the virtual height of the display to either 1080, 720 or 480, and the width is adjusted to maintain the aspect ratio.   So effectively we have for a 16x9 display, if the entire screen is filled a video that is:

[LIST]
[*]1080i = 1920 x 1080
[*]720p = 1280 x 720
[*]480i = 853 x 480
[/LIST]

Since 1080i & 720p for ATSC are assumed to be 16x9 there is no issue.  But for 480i there is a difference.  If we were talking about a regular 4:3 display, you are limited to a video that is 640 x 480.  So on the above TV on the 853 x 480 you end up with a video that has a width of 640 with two side bars that cover the rest of the 853 wide display field.  Commonly the broadcasters will send either 640x480 or 704x480.

However if the video is transmitted as 16:9, as in the sample I included above, then you would expect to see a displayed video that is 720 wide with smaller side bars. (or whatever width transmitted by the broadcaster up to 853. In this case it was 720) This is how the TV will display this type transmission.   However MythTV is treating the transmission as if it were transmitted 4:3 and I end up with a video that is 640 wide.  Since I assume the broadcaster did not intend for this, the video looks "squashed".  

I hope this is a better explaination.

---

### Post by tgm4883 on 2012-06-07
The video file posted is a 4:3 show with padded sides to make it 720x480. When I play this back at 720x480 it looks fine to me. When I measure the actual picture and do the math, it's 4:3. I see no reason this would have rectangle pixels, and the math backs that up? Sounds like you've been watching it incorrectly up until now and now that it is correct it looks off.

MythTV is doing exactly what it should with this video, play it back at 720x480.

---

### Post by tgm4883 on 2012-06-07
> **topcat5 said:**
> I just realized that I explained this incorrectly.  


Yes, we've been trying to tell you that.

> **topcat5 said:**
> 
I've done a crash course on aspect ratios in the last couple of days and don't do justice to what seems to be an amazingly complex subject.   I'll take another stab at it to try and to be more clear.  

There are 3 formats commonly sent by TV stations, 1080i, 720p and 480i.  There are also 2 common aspect ratios 16:9 & 4:3.  From what I can see the following assumptions are made.  1080i & 720p are 16:9 and 480i could be either.   


No. First, there are no assumptions being made. There simply doesn't need to be. MythTV can see the resolution of the file and knows what aspect ratio it is.

Secondly, when you talk about 1080i, 720p, and 480i (and 1080p, and 720i, and 480p) you are talking about vertical resolution. This has no bearing on whether it is 4:3 (1.33:1), 16x9 or anamorphic (2.35:1). 

> **topcat5 said:**
> 
When a TV sees these formats it will effectively set the virtual height of the display to either 1080, 720 or 480, and the width is adjusted to maintain the aspect ratio.   So effectively we have for a 16x9 display, if the entire screen is filled a video that is:

[LIST]
[*]1080i = 1920 x 1080
[*]720p = 1280 x 720
[*]480i = 853 x 480
[/LIST]

Since 1080i & 720p for ATSC are assumed to be 16x9 there is no issue.  But for 480i there is a difference.  If we were talking about a regular 4:3 display, you are limited to a video that is 640 x 480.  So on the above TV on the 853 x 480 you end up with a video that has a width of 640 with two side bars that cover the rest of the 853 wide display field.  Commonly the broadcasters will send either 640x480 or 704x480.


Mostly correct, but again there is no need for assumptions as MythTV knows the resolution it is and how to display that resolution.

> **topcat5 said:**
> 
However if the video is transmitted as 16:9, as in the sample I included above, then you would expect to see a displayed video that is 720 wide with smaller side bars. (or whatever width transmitted by the broadcaster up to 853. In this case it was 720) This is how the TV will display this type transmission.   However MythTV is treating the transmission as if it were transmitted 4:3 and I end up with a video that is 640 wide.  Since I assume the broadcaster did not intend for this, the video looks "squashed".  

I hope this is a better explaination.

Ah, this part does explain the issue a bit better. Your TV is 16x9 right? What does the following command return when you run it on your frontend.

```
xrandr
```

---

### Post by topcat5 on 2012-06-07
> **tgm4883 said:**
> The video file posted is a 4:3 show with padded sides to make it 720x480. **When I play this back at 720x480 it looks fine to me.** When I measure the actual picture and do the math, it's 4:3. I see no reason this would have rectangle pixels, and the math backs that up? Sounds like you've been watching it incorrectly up until now and now that it is correct it looks off.

MythTV is doing exactly what it should with this video, play it back at 720x480.Yes it takes a 740x480 window to display it properly given the way it's broadcast.     So my question is did you actually try this video in Myth displayed on a real TV?  

I agree with you 100% the video in that picture is 4:3.  I measured it as well.  So here is the problem.  For you to display it properly you had to have a 720x480 window as you indicated.    But on a TV where the setting is 4:3, you are limited to 640x480 the so video gets messed up.  

A real 720x480 window is not possible on a TV that is 4:3 or set to 4:3 as 720x480 = 3:2.

So the obvious fix for this is to set the video to 16:9. You end up with a DAR that I indicated above. This will make it possible to display the full 720x480 picture and this is why the broadcaster is transmitting it at this resolution. The engineer at the TV station referred to it as 480i converted to 16:9 anamorphic before transmission.

My issue is that for some reason MythTV thinks the DAR is 4:3, not 16:9 and thus what is displayed on the widescreen TV is 640x480 and not one that is 740x480.  I've tried changing it via the OSD controls and it will not correct the issue. It's as if the MythTV internal player sees "480i" and then automatically fixes the width to 640.

---

### Post by tgm4883 on 2012-06-07
> **topcat5 said:**
> Yes it takes a 740x480 window to display it properly given the way it's broadcast.     So my question is did you actually try this video in Myth displayed on a real TV?  

I agree with you 100% the video in that picture is 4:3.  I measured it as well.  So here is the problem.  For you to display it properly you had to have a 720x480 window as you indicated.    But on a TV where the setting is 4:3, you are limited to 640x480 the so video gets messed up.  

A real 720x480 window is not possible on a TV that is 4:3 or set to 4:3 as 720x480 = 3:2.

So the obvious fix for this is to set the video to 16:9. You end up with a DAR that I indicated above. This will make it possible to display the full 720x480 picture and this is why the broadcaster is transmitting it at this resolution. The engineer at the TV station referred to it as 480i converted to 16:9 anamorphic before transmission.

My issue is that for some reason MythTV thinks the DAR is 4:3, not 16:9 and thus what is displayed on the widescreen TV is 640x480 and not one that is 740x480.  I've tried changing it via the OSD controls and it will not correct the issue. It's as if the MythTV internal player sees "480i" and then automatically fixes the width to 640.

Please post the output of the xrandr command

---

### Post by topcat5 on 2012-06-07
> **tgm4883 said:**
> Please post the output of the xrandr commandSure.

:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1280x800       59.8  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
:~$

---

### Post by nickrout on 2012-06-07
This particular file has black borders top and bottom as well as at the sides, which confuses things.

I am at work now but playing with it at home last night showed (full screen on mplayer) narrow black bars at top and bottom and wider ones on each side. try mplayer -fs filename.mpg to see that for yourself.

Try mplayer -vf cropdetect filename.mpg to get the size of the black bars.

---

### Post by tgm4883 on 2012-06-07
> **topcat5 said:**
> Sure.

:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 290mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1280x800       59.8  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
:~$

What is your Fill, aspect ratio, and zoom settings at in the frontend?

---

### Post by nickrout on 2012-06-07
Actually it is not a 4:3 video, exract from mediainfo:

Video
ID                                       : 81 (0x51)
Menu ID                                  : 1 (0x1)
Format                                   : MPEG Video
Format version                           : Version 2
Format profile                           : Main@Main
...
Width                                    : 720 pixels
Height                                   : 480 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 29.970 fps

720/480=1.5, so it is anamorphic, ie it has non square pixels and the 16:9 flag tells the player to stretch it to 854x480  if no other scaling is applied. (480*16/9 = 853.333 but its more likely to use an even number so lets say 854)

Of course when you play it full screen it will also be then scaled to your screen resolution ie 1920x1080.

Now in the usual course part of that 16:9 video is black bands down each size because the source material IS 4:3, but the TV company (or someone before them in the chain) has added black bands so that it displays in the correct aspect ratio on a 16:9 display. That is fairly standard practice, although an alternative would be to transmit it with the 4:3 flag, no black bands and let the player sort out the aspect ratio.

This file is a bit more complex because some lummox has also added (narrower) black bands at the top and bottom. Try it in mplayer full screen, and you'll see what I mean.

---

### Post by topcat5 on 2012-06-08
> **nickrout said:**
> Now in the usual course part of that 16:9 video is black bands down each size because the source material IS 4:3, but the TV company (or someone before them in the chain) has added black bands so that it displays in the correct aspect ratio on a 16:9 display. That is fairly standard practice, although an alternative would be to transmit it with the 4:3 flag, no black bands and let the player sort out the aspect ratio.Yes indeed.  The TV engineer said it was done this way because it lets their marketing department use advertising that was laid for their 16:9 main HD channel on this channel as well.  albeit at 480i resolution.  If I look at the Myth playback information for the channel (live & recorded), it shows exactly what you are seeing, 720x480@29.97 

As I mentioned in my OP, all of the TVs, all widescreen, in the house handle it properly when receiving directly from the antenna.   The TVs will scale DAR to a height of 480 as you would expect to see for 16:9 480i and the width is 853 or 854.  The displayed video covers the entire vertical space.  I did notice the narrow black bands when looking at the video in mplayer that you mentioned, but the TVs do not show them as far as I can tell. 

MythTV on the otherhand does handle this video/channel in the same manner.  As I mentioned in the OP, it tries to scale it as if it were 4:3 480i instead of 16:9 480i, and I end up with a video that is only 640 wide.  Hence that video shows up somewhat distorted and smaller.   So my question is this something that I can change in the MythTV settings, or is it hard coded behavior that I will have to live with?

(thanks for taking the time to understand the problem)

---

### Post by nickrout on 2012-06-08
> **topcat5 said:**
> Yes indeed.  The TV engineer said it was done this way because it lets their marketing department use advertising that was laid for their 16:9 main HD channel on this channel as well.  albeit at 480i resolution.  If I look at the Myth playback information for the channel (live & recorded), it shows exactly what you are seeing, 720x480@29.97 

As I mentioned in my OP, all of the TVs, all widescreen, in the house handle it properly when receiving directly from the antenna.   The TVs will scale DAR to a height of 480 as you would expect to see for 16:9 480i and the width is 853 or 854.  The displayed video covers the entire vertical space.  I did notice the narrow black bands when looking at the video in mplayer that you mentioned, but the TVs do not show them as far as I can tell. 

MythTV on the otherhand does handle this video/channel in the same manner.  As I mentioned in the OP, it tries to scale it as if it were 4:3 480i instead of 16:9 480i, and I end up with a video that is only 640 wide.  Hence that video shows up somewhat distorted and smaller.   So my question is this something that I can change in the MythTV settings, or is it hard coded behavior that I will have to live with?

(thanks for taking the time to understand the problem)

I am using mythavtest and it seems to play it correctly. That is on my laptop screen, I will try it on the TV later.

---

### Post by topcat5 on 2012-06-09
> **nickrout said:**
> I am using mythavtest and it seems to play it correctly. That is on my laptop screen, I will try it on the TV later.
OK.  It will be interesting to know if you get it to work on a TV and what settings might be responsible for the difference.

---

### Post by nickrout on 2012-06-09
> **topcat5 said:**
> OK.  It will be interesting to know if you get it to work on a TV and what settings might be responsible for the difference.

what version of mythtv are you using?

---

