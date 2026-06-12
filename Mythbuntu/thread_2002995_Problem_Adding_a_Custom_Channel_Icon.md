---
title: "Problem Adding a Custom Channel Icon"
date: 2012-06-13
forum: Mythbuntu
---

### Post by johnvic on 2012-06-13
I am running 12.04/.25. It is a single PC setup, both backend and fronted in one.

I was able to successfully do this in 11.10. I did not upgrade but reinstalled. I am still learning, a lot!

I needed to add 2 custom channel icons. I created a directory called/usr/share/mythtv/icons. I found *.png icons on the internet and trimmed them to slightly smaller than 132x99. I copied those graphics to my mythbuntu desktop by mounting a usb stick, next step is sharing files over a network! I copied the *.png files to my previously created directory ( sudo cp ). Went into mythtv backend setup and entered the location of the files in the channel editor's icon, i.e. /usr/share/mythtv/icons/antennalogo.png. I tabbed to next and then finish and then escaped to leave setup, etc. 

I can see the icons in mythweb but not in the watch tv guide. Am I missing a step? Like I said, it worked in 11.10. Is there a new way now?

Thanks!

---

### Post by Lester_Burnham on 2012-06-13
Hi, 

Mine are located in /home/user/.mythtv/channels
User being current user.

Might only be a permissions issue.

Lester

---

### Post by johnvic on 2012-06-15
Thanks. I looked in that directory and am not seeing the two added icons. Also, the icons in the channels directory are all jpegs but I added png files. I'm not sure if I can just copy the files to that drectory and all will be hunky dory

---

### Post by Lester_Burnham on 2012-06-16
Hi,

If you move them, you need to update the path in the channel editor.
Permissions wise, they can be <user>:<user> or <user>:mythtv as your user should be in mythtv group anyway. Other than that it should work.

I re-read you first post and see they are in mythweb, so all I can think of is permissions, unless there is some setting to enable icon in guide.

Lester

---

### Post by johnvic on 2012-06-17
Firstly, thanks for your help and responses!

I tried setting the ownership and group to mythtv and to my account, etc., each time removing the icon and adding it fresh. But still no joy. I may be doing something wrong or it's a 12.04 things.

---

### Post by nickrout on 2012-06-17
> **johnvic said:**
> Firstly, thanks for your help and responses!

I tried setting the ownership and group to mythtv and to my account, etc., each time removing the icon and adding it fresh. But still no joy. I may be doing something wrong or it's a 12.04 things.


1. what is the putput of the following mysql query:

```
select chanid, channum, icon from channel
```

2. what is the output of ls -l /full/path/to/iconfile.png for each iconfile you cannot see.

3. perhaps pngs do not work. try ```
convert iconfile.png iconfile.jpg
``` then using the jpeg version.

---

### Post by johnvic on 2012-06-18
1. what is the putput of the following mysql query:

```
select chanid, channum, icon from channel
```

[COLOR="red"]I don't know how to do a mysql query, to be honest, but I'll look into it. What type of things should I be looking for in the query?[/COLOR]

2. what is the output of ls -l /full/path/to/iconfile.png for each iconfile you cannot see.

[COLOR="Red"]johnvic@JH-MythTV:~$ ls -l /usr/share/mythtv/icons/antennatv_logo.png
-rw-r--r-- 1 johnvic johnvic 14890 Jun 18 11:06 /usr/share/mythtv/icons/antennatv_logo.png
johnvic@JH-MythTV:~$ ls -l /usr/share/mythtv/icons/nonstop_logo.png
-rw-r--r-- 1 johnvic johnvic 28596 Jun 18 11:10 /usr/share/mythtv/icons/nonstop_logo.png
[/COLOR]

3. perhaps pngs do not work. try ```
convert iconfile.png iconfile.jpg
``` then using the jpeg version.

[COLOR="red"]I did try jpegs before but that did not solve it.

I also tried putting the icons in the same directory as the icons that mythtv does, /home/johnvic/.mythtv/channels. But that did not solve it. Just to be clear, every time I try a new thing, jpeg vs. png, icon directory, I change the file location in the channel editor.[/COLOR]

---

