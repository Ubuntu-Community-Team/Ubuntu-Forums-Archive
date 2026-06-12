---
title: "Audio Issues - Fresh Install 15.10"
date: 2018-03-07
forum: Multimedia Software
---

### Post by danialsmith49 on 2018-03-07
[COLOR=#000000]Long story short: I want to get [/COLOR][COLOR=#000000]the my[/COLOR][COLOR=#000000] audio to work in a fresh [/COLOR][COLOR=#000000]lubuntu[/COLOR][COLOR=#000000] install WITHOUT [/COLOR][COLOR=#000000]pulseaudio[/COLOR][COLOR=#000000].[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]Current status: [/COLOR]
[COLOR=#000000]I have a fresh install of [/COLOR][COLOR=#000000]lubuntu[/COLOR][COLOR=#000000] 15.10 on my [/COLOR][COLOR=#000000]htpc[/COLOR][COLOR=#000000].[/COLOR]
[COLOR=#000000]I connect the pc to my tv via an [/COLOR][COLOR=#000000]hdmi[/COLOR][COLOR=#000000] cable.[/COLOR]
[COLOR=#000000]I connect my speakers to the tv.[/COLOR]
[COLOR=#000000]I use [/COLOR][COLOR=#000000]kodi[/COLOR][COLOR=#000000] to watch/manage most of my media and the audio works just fine through [/COLOR][COLOR=#000000]kodi[/COLOR][COLOR=#000000].[/COLOR]
[COLOR=#000000]I installed chrome to watch amazon prime/[/COLOR][COLOR=#000000]netflix[/COLOR][COLOR=#000000]/youtube content. I currently have no audio in any of these settings.[/COLOR]
[COLOR=#000000]I also do not have audio when running the same content I run through [/COLOR][COLOR=#000000]kodi[/COLOR][COLOR=#000000] through the default system player, GNOME Mplayer.
I have done a lot of research in [/COLOR][[COLOR=#000000]software development services[/COLOR]]("http://www.topindigixpert.com/software-development-services.php")[COLOR=#000000] regarding this issue but didn't get any helpful answer.[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]I have previously tried fixes like those found in these threads:[/COLOR]
[COLOR=#000000]http://ubuntuforums.org/showthread.php?t=2280056[/COLOR]
[COLOR=#000000]http://ubuntuforums.org/showthread.php?t=2279687[/COLOR]
[COLOR=#000000]http://ubuntuforums.org/showthread.php?t=2240335[/COLOR]
[COLOR=#000000]http://askubuntu.com/questions/56293...stall-no-sound[/COLOR]
[COLOR=#000000]http://ubuntuforums.org/showthread.php?t=2232938[/COLOR]
[COLOR=#000000]http://ubuntuforums.org/showthread.php?t=2001545[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]All of these solutions involve installing [/COLOR][COLOR=#000000]pulseaudio[/COLOR][COLOR=#000000]. While this gives me audio everywhere, it introduces a new set of problems, every time, whose solutions have eluded me. I'm sick of going down that rabbit hole of configuration files and cryptic setting tweaks. The audio in [/COLOR][COLOR=#000000]kodi[/COLOR][COLOR=#000000] works out of the box without [/COLOR][COLOR=#000000]pulseaudio[/COLOR][COLOR=#000000], so, unless somebody shows me otherwise, I have every reason to believe I can get the audio to work elsewhere without [/COLOR][COLOR=#000000]pulseaudio[/COLOR][COLOR=#000000]. [/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]Please, help! I might be slow to reply, but I'll follow any instructions or post any details that you ask me for. Your patience and expertise [/COLOR][COLOR=#000000]is[/COLOR][COLOR=#000000] humbly appreciated.[/COLOR]

---

### Post by jeremy31 on 2018-03-07
You might want to install a supported Lubuntu version, 15.10 has been EOL since August 2016, 16.04 is Long Term Support and 17.10 is supported until August 2018

---

### Post by coffeecat on 2018-03-07
Welcome to the forum.

15.10 is out of support. The repositories closed in 2016, which means that you will not get updates, most critically security updates. Please install a supported version of Lubuntu. 

Also - you included 6 links in your post. The forum software automatically converts URLs into hyperlinks for the convenience of other forum members. Somehow you have managed to subvert the best efforts of the software and all that is visible in your post are bare URLs. This is perhaps because you have liberally included quite unnecessary BBCode color tags. Please use only the default font properties, unless you need to highlight something. That way you are less likely to undo useful functionality in your posts.

---

### Post by Yellow Pasque on 2018-03-07
If you don't want pulseaudio, you're probably better off using a minimal Debian install or Arch Linux or something like that. As others have pointed out, running an EOL release is a bad workaround.

I run xfce on Debian without pulseaudio on my main box. I do have to use pulse emulation ("apulse") to get sound in Firefox.

As to why sound doesn't work in your current setup, it's hard to say. Maybe it's because you don't have the correct output/device selected in gnome-mplayer. As for Chrome, it may be trying to send the audio to whatever device is index 0, which usually isn't HDMI audio that you're trying to use.

---

### Post by monkeybrain20122 on 2018-03-07
Firstly like others said 15.10 is long dead. Secondly when was the last time you used Ubuntu and had problems with pulseaudio? I remember there were some hue and cry about pulseaudio but that was YEARS ago, all those "how to get rid of pulseaudio" tutorials on the internet are super old. I have never had a problem on a variety of machines and distros.

---

### Post by coffeecat on 2018-03-08
I&#8217;m sorry that those who attempted to offer help have had their time and goodwill abused, but this is not someone who will be coming back &#8211; at least with this forum account; I have made certain of that. Have a look at this:

[https://ubuntuforums.org/showthread.php?t=2318038](https://ubuntuforums.org/showthread.php?t=2318038)

Looks familiar?

Is the OP of this thread what the forum staff refer to as a proto-spammer? A troll? Someone who needs to get out more? We shall never know. Someone who knows how to copy-paste? Most certainly. 

Thank you to all who contributed. I&#8217;ve closed the thread but, unusually, I&#8217;m leaving it in place for the time being. If only for the edification of forum members who may not know of some of the nonsense forum staff have to deal with.

---

