---
title: "sound works in either vista or 8.10, never both"
date: 2009-02-22
forum: Multimedia Software
---

### Post by oarking on 2009-02-22
3 months ago: installed 8.04 on a fresh partition next to vista ultimate. updated everything, worked beautifully. no sound or video issues. reboot into vista and there's no sound at all. so i pop in the cd that came with my motherboard and reinstalled the drivers. after reboot it worked just fine so i checked the sound in ubuntu and it worked too. then i reboot back into vista and there's no sound yet again so i install the drivers again and it works fine. repeat.

1 week ago: upgraded to 8.10 and reinstalled vista as well. whenever i restart vista at all there's no sound, it will only work if i install the drivers and say "reboot later". as long as i don't restart my computer it works fine. so i get the updated drivers and now i can restart my computer without any issues at all. so i hop over to ubuntu to play around for a while and pop on the radio in amarok and the sound works perfectly. then i try to watch some youtube videos but all i can hear is the music from the videos not the dialog. so i open up an avi in vlc and it's the same thing. music is fine but the dialog volume is so low i can barely hear it. same thing with totem. i'm afraid to reinstall the drivers in ubuntu because it'll break my vista audio again. there's no updated drivers for linux for my soundcard.

my motherboard is the asus p5k-e wifi AP with onboard 8-channel hd audio. the drivers on the cd/website are soundmax. what the heck is going on? sorry about the long post but as you can see this isn't the typical audio issue.

---

### Post by Mercury_Alpha on 2009-02-22
Your audio in Ubuntu is apparently having issues because ALSA isn't really set up properly by default to handle multiple audio streams. To correct that, refer to this thread: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

As for why your sound in Vista disappears when you reboot, that looks like a Microsoft support issue. There's no way I know of that installing Ubuntu would effect your sound in Windows.

Also, the p5k-e apparently has a history of sound glitches.

---

### Post by oarking on 2009-03-11
sorry it took me so long to get back. i asked a friend of mine and he said that the audio drivers are stored at a hardware level so if the one for ubuntu conflicts with the one for vista then they'll fight for dominance. usually with ubuntu winning like in this case.

the fix i used was uninstalling then reinstalling all the audio drivers in ubuntu, all the same ones. then i went to the asus website and used the driver one step back from the most current one and everything suddenly worked totally fine. i guess i just won't update any of my audio drivers from now on.

thanks for you reply, good luck to everyone else.

---

