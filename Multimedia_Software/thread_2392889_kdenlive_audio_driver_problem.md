---
title: "kdenlive audio driver problem"
date: 2018-05-26
forum: Multimedia Software
---

### Post by robilio on 2018-05-26
Hello,
I'm on kubuntu 18.04 and I've got a problem with kdenlive.
I had a problem with the audio, I could not ear anything inside kdenlive. So I went to the Settings > Configure > Playback menu and I tried the variuos options "Audio driver", and from the moment I set "SDL" and "OSS with DMA access", when I start kdenlive I get the error message[INDENT][I]Could not create the video preview window.
[/I][/INDENT]
[INDENT]*There is something wrong with your kdenlive install or your driver settings, please fix it.*
[/INDENT]

The original settings of the Playback were "Audio backend"=SDL and "Audio Driver"=Automatic. But now if I set them in the same way kdenlive crashes and when I restart it the setting goes back to "OSS with DMA access".

If I start kdenlive from the terminal I get these messages:
```
[consumer sdl2_audio] Failed to initialize SDL: Audio target 'dma' not available
QXcbConnection: XCB error: 8 (BadMatch), sequence: 9649, resource id: 10486110, major code: 130 (Unknown), minor code: 3
QXcbConnection: XCB error: 8 (BadMatch), sequence: 9681, resource id: 10486110, major code: 130 (Unknown), minor code: 3
QXcbConnection: XCB error: 8 (BadMatch), sequence: 9684, resource id: 10486110, major code: 130 (Unknown), minor code: 3
QXcbConnection: XCB error: 8 (BadMatch), sequence: 9700, resource id: 10486110, major code: 130 (Unknown), minor code: 3
```

I have already uninstalled and reinstalled kdenlive, also with "apt purge kdenlive", but without success...

What can I do to go back to a fresh install of kdenlive with all its original settings?

Thankx!
R.

---

### Post by robilio on 2018-05-26
:redface: Sorry to have posted an already answered question...
The solution was not far away: [https://ubuntuforums.org/showthread.php?t=2390771&highlight=kdenlive](https://ubuntuforums.org/showthread.php?t=2390771&highlight=kdenlive)

Delete folders:
~/cache/kdenlive
~/.local/share/kdenlive
 and delete file
~/.config/kdenliverc

Anyway thank you for the precious forum!

Bye,
R.

---

