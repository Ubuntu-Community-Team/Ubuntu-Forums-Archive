---
title: "Get-iplayer"
date: 2016-10-18
forum: Multimedia Software
---

### Post by Y^2om&amp;#7sgP on 2016-10-18
Hi all, hope I'm posting this in the correct area, if not please move ;)

I use get-iplayer to download BBC programs for watching off line, and up until a couple of weeks ago files were in the region of 600Mb.  Then things suddenly (it appeared) went a little wrong and downloads now come in at around 1-2 Gb.  This is for a 30 minutes program.

Can anyone shed any light please?

Thank you in advance

---

### Post by howefield on 2016-10-18
This thread should help you..

[https://ubuntuforums.org/showthread.php?t=2336007](https://ubuntuforums.org/showthread.php?t=2336007)

---

### Post by Y^2om&amp;#7sgP on 2016-10-18
Brilliant, thanks for that howefield, I'll give it a go :)

---

### Post by howefield on 2016-10-18
You're welcome, feel free to mark the thread as solved if it is ;)

---

### Post by ajgreeny on 2016-10-18
Here is the get-iplayer web-page with all the info you might like to see the many options available for both video and audio options.
[https://github.com/get-iplayer/get_iplayer/wiki/modes](https://github.com/get-iplayer/get_iplayer/wiki/modes)

I have set several aliases for the different qualities available and use them depending on the quality of output file that I want for a particular programme as there's no point recording HD quality when it is just a news or discussion or similar programme.
```
alias gip='get_iplayer'
alias gipg='get_iplayer -g --tvmode=tv25fps --file-prefix="<nameshort><-senum><-episodeshort>"'
alias gipgbetter='get_iplayer -g --tvmode=better --file-prefix="<nameshort><-senum><-episodeshort>"'
alias gipghd='get_iplayer -g --file-prefix="<nameshort><-senum><-episodeshort>"'
alias gipi='get_iplayer --info'
alias giplive='get_iplayer --type=livetv --get'
alias gipr='get_iplayer --type radio'
```
The use of ```
--file-prefix="<nameshort><-senum><-episodeshort>"
``` in these "get" aliases means the files are named properly for the PlexMediaserver that I use to stream media to two set-top boxes (Now-TV) I use on non-smart TVs.

Here also is a txt file I have saved in my home as a reminder of these video and audio quality options.
```
Get_iplayer TV Recording modes.

Max Resolution 	Max Frame Rate 		Max Bit Rate 	Max Quality Configuration 				Notes
1280x720 		50fps 		5Mbps 		get_iplayer --prefs-add --tvmode=best 		gipghd	default
960x540 		50fps 		3Mbps 		get_iplayer --prefs-add --tvmode=better 	gipgbetter
1280x720 		25fps 		2.5Mbps 		get_iplayer --prefs-add --tvmode=tv25fps 	gipg
960x540 		25fps 		1.7Mbps 		get_iplayer --prefs-add --tvmode=vgood 	
704x396 		25fps 		950kbps 		get_iplayer --prefs-add --tvmode=good 	
512x288 		25fps 		550kbps 		get_iplayer --prefs-add --tvmode=worse 	
384x216 		25fps 		340kbps 		get_iplayer --prefs-add --tvmode=worst 	

NOTE: For TV, the resolution and bit rate of available streams may vary slightly at a given quality level. The best variants are always tried first. Higher-quality streams may not be available for all programmes.

Get_iPlayer Radio Recording modes

Max Bit Rate 	Max Quality Configuration 					Notes
320kbps 		get_iplayer --prefs-add --radiomode=best 		default
128kbps 		get_iplayer --prefs-add --radiomode=better 	
128kbps 		get_iplayer --prefs-add --radiomode=vgood 		same as better
96kbps 			get_iplayer --prefs-add --radiomode=good 	
48kbps 			get_iplayer --prefs-add --radiomode=worse 	
48kbps 			get_iplayer --prefs-add --radiomode=worst 		same as worse 	
```

---

### Post by Y^2om&amp;#7sgP on 2016-10-20
Thanks for the update ajgreeny, really helpful, I've taken a copy of the file and saved to my home folder for future reference

Thanks again for the help guys...Issue solved :P

---

### Post by shantiq on 2016-10-23
thanks for this Greeny as frankly 50fps is serious overkill :::   how much definition does anyone need

> get-iplayer --prefs-add   --tvmode=tv25fps

---

