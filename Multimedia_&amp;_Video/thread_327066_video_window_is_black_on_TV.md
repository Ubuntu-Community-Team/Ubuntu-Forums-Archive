---
title: "video window is black on TV"
date: 2006-12-28
forum: Multimedia &amp; Video
---

### Post by tregor29 on 2006-12-28
Hello,

I have a laptop with a ATI Radeon 9600 card and I'm trying to set up TV-Out on Edgy.
I followed the  [BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI?action=fullsearch&value=linkto%3A%22BinaryDriverHowto%2FATI%22&context=180"). Now all is ok - I see my desktop perfectly on the tv screen - except one thing : when I open a video player (like mplayer), I see the movie on my laptop, but on tv the player's window remains hopelessly black.

Thanks for any help

---

### Post by KenSentMe on 2006-12-28
On most laptops there's a function key to make an external screen the default screen. The default screen is the one where the video will be displayed. Look in your manual and check if there's a key to switch screens (perhaps fn+F4 or fn+F8). Don't know for sure, but it might solve your problem.

---

### Post by tregor29 on 2006-12-28
The thread's title isn't very good. I've no problem to see on my TV that what I see on my laptop except when I open a video player, like mplayer or kaffeine, the player's window - and not others windows - remains black on the tv

---

### Post by KenSentMe on 2006-12-28
Still, try the option i suggested. I had a presentation with a laptop on a big screen once and it didn't display the video too (the rest looked fine). When i switched with the fn key to the external screen, the video worked fine on the external screen.

---

### Post by tregor29 on 2006-12-28
If it's the unique solution I have a big problem. My laptop - an asus M6NE - freeze (on Edgy) when I press Fn+F8 (the "switch screen" button).

Thank you for your help.

---

### Post by tregor29 on 2006-12-28
I found a workaround for the problem with my "switch screen" button (thanks to  NicolòChieffo for his M6 [tutorial]("https://wiki.ubuntu.com/LaptopTestingTeam/AsusM6800Ne") But when I press Fn+F8 the tv screen flicks on for a moment ... and the mplayer's area remains black

Any ideas ?

---

### Post by tregor29 on 2006-12-29
It's OK ! The solution was the video output drivers of mplayer, whith "mplayer -vo gl" the mplayer's window is fine on tv screen.

---

