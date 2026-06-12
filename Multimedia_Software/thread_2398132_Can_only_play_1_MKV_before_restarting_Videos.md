---
title: "Can only play 1 MKV before restarting Videos"
date: 2018-08-07
forum: Multimedia Software
---

### Post by jhite-h on 2018-08-07
I don't know how else to explain it. If I watch 1 .mkv video in "Videos" and let it finish I can not watch another without force closing the application. If I try to watch a second video after the first finishes it loads the title but that's it. Videos completely locks up. I have to choose quit by right clicking on the icon, then wait about 5 seconds and it will pop up and say it's not responding and I have to force close. Then and only then can I start the second video. It will load and play just fine. When it finishes, same story again. The file doesn't matter, does it for pretty much every .mkv as far as I have noticed.

---

### Post by Yellow Pasque on 2018-08-07
If you start the program in the terminal, do you get any helpful error messages?
```
totem
```

---

### Post by jhite-h on 2018-08-08
I'll have to run through a whole video to see, but so far the only errors I see are about font in the subtitles.

---

### Post by mc4man on 2018-08-08
Try opening totem & multiple videos from terminal, then either let it play thru them or you can use the Next.. & Previous.. buttons to switch back & forth. Any issues that way and if so what's in the terminal at that point?
i.e,
> totem --enqueue  /path/to/vidname1 /path/to/vidname2

---

### Post by jhite-h on 2018-08-09
Sorry, thanks for the suggestions. I haven't actually had time to sit  down and watch through two full 45 minute videos back to back yet to  test things. 
I tried a couple shorter ones from terminal but it  didn't do it so it's either a timing thing, or it just doesn't do it  when I start from terminal. Can't be sure yet.

---

### Post by jhite-h on 2018-08-09
Perhaps I need to load one file from terminal then try to start the second one after and see what error I get? Maybe starting totem then loading a video won't recreate the problem?

---

### Post by mc4man on 2018-08-09
You can remove terminal by using shift+left click to highlight 2 or more vid files then right click > open with Videos
As soon as Videos opens you can switch vids thru the buttons.

---

### Post by jhite-h on 2018-08-10
Honestly, I haven't had any luck reproducing this through any method of command line launching it. But I can get it to happen every time if I launch the video from the firefox download manager and then launch another after. How can I get the output for a program that wasn't started in terminal to display in terminal?

---

### Post by jhite-h on 2018-08-11
Spoke too soon. I got it to crash after loading a file form terminal, watching it, then loading another from the firefox download manager. I got this error:   (totem:16193): GLib-CRITICAL **: 09:17:29.083: g_key_file_load_from_file: assertion 'file != NULL' failed

Although, this was exactly like other times, because I could still close totem by click the X. Normally I have to right click on the icon in the menu and select Quit, then when it pops up select Force Close. So I'm not sure if this has gotten me anywhere.

---

