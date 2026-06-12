---
title: "SA Firewire recordings not able to be transcoded"
date: 2010-03-07
forum: Mythbuntu
---

### Post by Calmor on 2010-03-07
I have a SA4250HDC that, largely, plays nice with my system.  My problem lies in that the channel changing often takes longer than the recorder thinks, so the .mpg file starts before the operation is fully complete.  On playback, I'll get a little of the show from the previous channel, then blank for a moment, before going onto the show I wanted.

In transcoding, however, ffmpeg refuses to get past those first few frames.  I get between 55 and 80 frames transcoded (varies by file), then the whole process stops.  ffmpeg doesn't crash, it just sits there, fps rate dropping, until I kill it.  Adding flags to skip frames and/or time don't seem to help, it still sticks in the same spot.

MythWeb's flash player also cannot play past the glitch.

I'm assuming it has to do with the channel changing, and bad data.  I'm willing to live with the effects, if there's some way I could transcode or repair the file.

In some cases, I think the format may be changing, but in many, it's the same in the previous and current shows.  (In some cases, the previous channel was SD, then switching to HD... But not every case)

Any suggestions?  I'm game to try modifying the channel change delay, running some script/program to smooth out the file, etc... But I haven't found a way to do the latter, and know little of the former.

(System is 9.04 x64 running J.Y. Avenard's 0.21 repo.)

---

