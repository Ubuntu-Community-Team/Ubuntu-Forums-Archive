---
title: "tv_grab_nl not working in mythbuntu"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by meinthiemstra on 2007-10-24
During the installation of Mythbuntu 7.10 when entering the Video Sources and selecting Holland for xmltv program grabbing the system hangs on a progress screen staying on 50% for ever. I have overcome this issue by selecting no grabber, the installation completes and most functions work.

When I do, in a terminal screen, *tv_grab_nl --configure* later on, the tv_grab_nl.conf file is build, when I do *tv_grab_nl* the program data comes in fine. The command *mythfilldatabase* should now load the program guide but nothing happens.

Where do I find the grab file stored?
Any help or suggestions to resolve this issue?

Thanks

---

### Post by verhage on 2007-11-06
I'm currently re-installing my htpc using mythbuntu. Before, I have been using mythtv on a 7.04 regular ubuntu desktop.

For grabbing tv guide data in Holland it's preferrable to use the tv_grab_nl_py, which is to be found here:

[http://graphics.tudelft.nl/~paul/grabber/]("http://graphics.tudelft.nl/~paul/grabber/")

It is a much faster grabber than the default tv_grab_nl and captures channel logos by default.

The default grabber is located at /usr/bin. To use tv_grab_nl you can simply remove MythTV's default grabber and replace it with tv_grag_nl_py (of course renamed to tv_grab_nl), or create a symlink if you like.

This has worked for me perfectly before. I'm not that far in the installation process right now (had to reboot after bumping into the 50% hanging problem :().

Off topic:
I think it's rather strange that Mythbuntu creates an Ext3 video data partition by default; as XFS or ReiserFS are highly recommendable!

---

### Post by verhage on 2007-11-12
And I have a solution to our little problem :)

Somewhere somehow, the interaction between mythfilldatabase and tv_grab_nl isn't completely honky dory. However, we can just grab the tv guide data, write it to file and use mythfilldatabase to store the xml data into the mythconverg database:

```

tv_grab_nl --output listings.xml

```

This grabs the tv-data and writes it to file listings.xml. Now, let's use this file as in input for mythfilldatabase:
```

mythfilldatabase --file 1 -1 listings.xml

```

To automate the process, put these to lines in a shell script (make it executable with chmod ugo+x). Log in as the user that is supposed to run the script and type:

```

crontab -e

```

My script runs every night at 1:00 AM. In a cron expression this would be:

```

0 1 * * * /wheremyscriptis/my_script.sh

```

Et voila :)

---

