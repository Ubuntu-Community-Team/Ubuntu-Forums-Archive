---
title: "Problems Installing Gimp Plugins"
date: 2012-05-24
forum: Multimedia Software
---

### Post by Valkyr333 on 2012-05-24
I want to install some of the optional plugins for GIMP Image Editor. I've gotten as far as downloading the .scm files, but Kubuntu won't let me copy them to the necessary folders, which every "how-to" on the subject tells me to do. I tried downloading the .scm's directly to /home/username/.gimp-2.6/scripts, but when I clicked "OK" nothing happened. Then I tried downloading them to my "downloads" folder, dragging and dropping them into /home/username/.gimp-2.6/scripts or /usr/share/gimp/2.0/scripts and I was given the "Access denied!" message.

Is there a terminal command (for instance, using sudo to get around the folder's defensiveness)  that will install the files there?

Thanks for any help you can give...

---

### Post by kc1di on 2012-05-24
> **Valkyr333 said:**
> I want to install some of the optional plugins for GIMP Image Editor. I've gotten as far as downloading the .scm files, but Kubuntu won't let me copy them to the necessary folders, which every "how-to" on the subject tells me to do. I tried downloading the .scm's directly to /home/username/.gimp-2.6/scripts, but when I clicked "OK" nothing happened. Then I tried downloading them to my "downloads" folder, dragging and dropping them into /home/username/.gimp-2.6/scripts or /usr/share/gimp/2.0/scripts and I was given the "Access denied!" message.

Is there a terminal command (for instance, using sudo to get around the folder's defensiveness)  that will install the files there?

Thanks for any help you can give...

the terminal command for copying a file is cp

here how it would look for what your trying to do.
Though if the destination is into your home directory us should not need root privilaged to do it for some reason it seems like you do so I'll do it that way :

```
sudo cp /home/<usr name>/Downloads/<filename> /home/username/.gimp-2.6/scripts
```

* note: replace <usr name> with yours and <filename> witht he actual file name. 

if you want to move the file there it's exactly the same except you would use ```
mv
``` instead of cp.

Good luck

---

### Post by Valkyr333 on 2012-05-24
> the terminal command for copying a file is cp

here how it would look for what your trying to do.
Though if the destination is into your home directory us should not need  root privilaged to do it for some reason it seems like you do so I'll  do it that way :

 	Code:
 	sudo cp /home/<usr name>/Downloads/<filename> /home/username/.gimp-2.6/

Thanks for replying. I did this, but nothing seems to have changed. I realized I forgot a detail from earlier - I managed to add a file with the same name and copied the "code" part of the downloaded file into it manually earlier. I don't remember how I did that, but it didn't get results. When your advice from above didn't work with that file, I tried it on another plugin/script and it did work for that one. I'm assuming then that the presence of an identically-named file in the target directory is preventing the copy from being made. What would I do to purge that file so I can follow your instructions with respect to the original file?

---

### Post by kc1di on 2012-05-24
It should have given you a message that file already exists.

the command for removing a file is rm

thus would look something like this.
```
sudo rm /home/username/.gimp-2.6/scripts/<filename>
```

you may want to go to this page and print a copy to keep on hand :) 
[http://ss64.com/bash/]("http://ss64.com/bash/")

---

### Post by Valkyr333 on 2012-05-24
Ah, I've got it now.

It turns out I was looking in "Filters" rather than "Tools," so that was my mistake. Thank you very much for the info, though. I'm sure the other things you said will come in handy in other operations. =)

---

