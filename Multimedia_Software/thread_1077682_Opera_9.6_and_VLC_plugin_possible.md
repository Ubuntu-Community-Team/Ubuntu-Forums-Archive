---
title: "Opera 9.6 and VLC plugin possible?"
date: 2009-02-22
forum: Multimedia Software
---

### Post by RavanH on 2009-02-22
Hi,

Has anyone got the latest Opera (9.63 at time of writing) *and* can watch video streams with VLC ? 

After installing the VLC plugin with ```
sudo apt-get install vlc mozilla-plugin-vlc
``` it is running succesfully on Firefox. But not Opera, even though it is listed under the opera:plugins and I have set this plugin as the default action for various media formats under Toold > Preferences... > Advanced > Downloads. Opera refuses to use VLC and sticks to the Gecko Media Player plugin which I installed following the [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683"). I am not unhappy with that result but would like it even better when I could get Opera (best browser EVER ;) ) and VLC working.

Anyone any suggestion? Thanks :)

---

### Post by wolfen69 on 2009-02-22
[This]("http://groups.google.com/group/opera.linux/browse_thread/thread/cb664acb7906fae9") page has *some* answers.

---

### Post by RavanH on 2009-02-22
> **wolfen69 said:**
> [This]("http://groups.google.com/group/opera.linux/browse_thread/thread/cb664acb7906fae9") page has *some* answers.

Thanks wolfen, for the link. Only I already found that and similar treads. The thing is that Opera DOES recognize and list the pluginbut when it is selected as default action (for WMV files for example) the streams still get played in the other option available. Currenly that other option is Gecko Media Player but when I had the totem plugin or the mplayer plugin installed, Opera would play in those :(

I searched for anything related on the internet but cannot find answers. 

Do you have Opera with working VLC plugin?

---

### Post by sophtpaw on 2009-06-25
Like most people i already had flash installed. It sits in:

 /usr/lib/flashinplugin-installers

I installed Opera 9.6 and then cd'd to the flash folder above. Then copied libflashplayer.so to usr/lib/opera/plugins, like so:

sudo cp libflashplayer.so /usr/lib/opera/plugins/

Seems to work. I don't know if there is another and/or better way?

---

### Post by RavanH on 2009-06-28
> **sophtpaw said:**
> Like most people i already had flash installed. It sits in:

 /usr/lib/flashinplugin-installers

I installed Opera 9.6 and then cd'd to the flash folder above. Then copied libflashplayer.so to usr/lib/opera/plugins, like so:

sudo cp libflashplayer.so /usr/lib/opera/plugins/

Seems to work. I don't know if there is another and/or better way?

Sorry sophtpaw, my question was about the VLC media player plugin. Not flash. Flash support came 'out of the box' on my 32bit setup since I have flashplugin-installer installed which puts the libflashplayer.so in /usr/lib/mozilla/plugins, where Opera looks for plugins too (at least in my case). On my 64bit system, I am trying the Opera 64bit 10alpha version which did nothing with the 32bit flashplayer. Luckily, there is an alpha version of flash 64bit around these days and it workes just dandy :)

Anyway, back to my VideoLAN Client plugin... Anyone around with a solution or who can at least confirm a working combo of Opera (either 9.6 or 10.0alpha) and VLC?

---

### Post by ceciliaFX on 2009-06-28
I use the VLC plugin with no problem. If I recall you have to go to preferences/Advanced /Downloads and make sure the formats you wish to use VLC have it marked.

---

### Post by RavanH on 2009-11-18
> **ceciliaFX said:**
> I use the VLC plugin with no problem. If I recall you have to go to preferences/Advanced /Downloads and make sure the formats you wish to use VLC have it marked.

That is exactly what I did but still Opera chooses any other available player plugin. If no other player, no play :(

This problem persist in Opera 10.01 for me... Anyone?

---

### Post by suoko on 2010-01-21
problem here too
apple trailer does not see any plugin apparently

---

