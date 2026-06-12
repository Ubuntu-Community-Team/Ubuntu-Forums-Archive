---
title: "Bright screen"
date: 2006-05-24
forum: Multimedia &amp; Video
---

### Post by jonttix on 2006-05-24
when I have finished my installation and the program starts, the screen is so bright that i can´t see anything. What should i doo? You hear sounds when you use the keyboard. I have a acer aspire 5024WLMi with a ati x700 graphics card.
Any clue?

---

### Post by xyz on 2006-05-24
Hi-
There's something here about brightness:
[http://www.ubuntuforums.org/showthre...ght=brightness](http://www.ubuntuforums.org/showthre...ght=brightness)

I have a Toshiba Satellite A40 and use this command line to adjust:
Code:

echo 'brightness : 1' > /proc/acpi/toshiba/lcd

in root. The number "1" is what you may want to change. Hope this helps you.
__________________

---

### Post by jonttix on 2006-05-25
I´m very new too linux, how do I do that?

---

### Post by xyz on 2006-05-25
Hi-
Sorry I didn't realize you are new to this. I am too, by the way.
Place your cursor on Application (top left screen)click on it to go to Accessories and scroll down to Terminal and click. In it, type:
```
sudo echo 'brightness : 1' > /proc/acpi/acer/lcd

```
Press Enter - It'll then ask your password, type it in and Enter again.
Now **REMEMBER** this: This works for me on a Toshiba Satellite A40. I have NO idea if it'll do the trick on yours! Give it a try, it won't kill your machine.

Also I've done a little research for you:
[http://www.pocket-lint.co.uk/review.php?reviewId=1271](http://www.pocket-lint.co.uk/review.php?reviewId=1271)

You may want to become a member of that site so that you could then ask about brightness directly on an Acer site. Let us know what you find out.

If you don't understand something, do ask again even if you think it's stupid. Most of us have gone through this or ...still are.
Good luck.

---

### Post by xyz on 2006-05-26
There is a whole thread about your laptop. You might just learn something there; I didn't read il all the way through.
[http://ubuntuforums.org/showthread.php?t=46853&highlight=acer+aspire+5024WLMi](http://ubuntuforums.org/showthread.php?t=46853&highlight=acer+aspire+5024WLMi)

---

