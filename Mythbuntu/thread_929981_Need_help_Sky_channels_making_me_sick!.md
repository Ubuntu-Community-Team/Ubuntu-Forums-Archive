---
title: "Need help Sky channels making me sick!"
date: 2008-09-25
forum: Mythbuntu
---

### Post by singedwings on 2008-09-25
I hope someone can help me get the channels set up correctly for my Sky system. Mythbuntu is a great leap forward, but the whole tv guide data set up is still an impenetrable mess.

I have a mythbuntu computer receiving my tv into the composite port from a sky digibox. I have got everything set up apart from the channel guide and changing channels.

To get the channel guide setup I have been working from [http://www.knoppmythwiki.org/index.php?page=SkyDigiBox]("http://www.knoppmythwiki.org/index.php?page=SkyDigiBox") which at least makes sense to me and [http://www.pebble.org.uk/linux/mediapcsw]("http://www.pebble.org.uk/linux/mediapcsw"). I have got to this point:-

"Now run this script to parse the matched_channels file and update the sql database with all those channels.

./update_channels matched_channels"

In the ubuntu specific guide it says "I had to edit the updatechannels.pl file to add '-u root -p my_mysql_root_password' to the mysql lines" but I have no idea how to do this properly and everything I have tried ends up with:-

"tellybox@tellybox-desktop:~$ ./update_channels matched_channels
bash: ./update_channels: Permission denied"

This is very frustrating so any help gratefully received.:confused:

---

### Post by singedwings on 2008-09-27
Alternatively if someone knows a better way to get the channels working or a good how to that would be fantastic as well.

---

### Post by singedwings on 2008-10-01
bump

---

### Post by laga on 2008-10-01
> **singedwings said:**
> 

"tellybox@tellybox-desktop:~$ ./update_channels matched_channels
bash: ./update_channels: Permission denied"


I have no clue about Sky. But try this:

```
chmod +x ~/update_channels
```

That sets the executable bit on the script so it's actually run.

---

### Post by singedwings on 2008-10-03
Thank you Iaga, that does seem to have solved my problem. The script now appears to work, although I think I may have messed something else up with all the tinkering I tried. I am going to start again and see if I am successful now.:)

---

