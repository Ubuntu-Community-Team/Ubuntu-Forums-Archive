---
title: "How I solved my black screen problem"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by lexarrow on 2007-07-10
Originally posted [here]("http://ubuntuforums.org/showthread.php?t=492192") . I've seen a lot of people have this (or similar) problem so I felt the need for a dedicated thread.

I'm sing Feisty on an Intel graphics card

Try this at your own risk. It worked for me, but I cannot guarantee it will work for others. My assumption is that if startx gives you an interface, this howto should work.

Here's my solution:

1.Go into recovery mode and type at the command line:

```
sudo apt-get remove xorg gdm
```

2. Now it's time to remove all xorg.conf files. Type:
```
startx
```
wait for the interface to load

3. Go to File system/etc/X11/ and erase all files that contain xorg.conf

4. Log out

5. At the command line type:

```
sudo apt-get install xorg gdm
```

6. Type

```
/etc/init.d/gdm restart
```

Now you should have your GUI back

Good luck!

---

