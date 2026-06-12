---
title: "Issues with Songbird Audio Player"
date: 2009-11-27
forum: Multimedia Software
---

### Post by LequidMetal on 2009-11-27
Songbird Audio player is not available in the ubuntu repos so i had to download and install it manually using the tar.gz file . I have created a launcher in the desktop and the "Applications>Sound and Video" Menu . 

My problem is that , it doesnt appear in the "Open With" right click menu . When i select Openwith>Other Applications there is no Songbird even though there is every other application installed in my buntu system :o . Is there a way i can get it into that menu/list ?

---

### Post by NoaHall on 2009-11-27
Yes, just simply browse to the songbird file, from "Preferred applications " and then add it.

---

### Post by krendar on 2009-11-27
I would like to add that it is on the Getdeb repository:

[http://www.getdeb.net/updates/#how_to_install]("http://www.getdeb.net/updates/#how_to_install")

After following the instructions all you need to do is:

```

sudo apt-get update
sudo apt-get install songbird
```

---

### Post by LequidMetal on 2009-11-28
> **NoaHall said:**
> Yes, just simply browse to the songbird file, from "Preferred applications " and then add it.

Spent a lot of time tinkering around with "Preferred Applications" couldnt find the browse button . Found an easier way though 

Right click on an audio file select "Properties > OpenWith > Add > Custom Command > Browse" and select the Songbird executable . Songbird automatically becomes the default application for that particular file type and it also turns up in the open with menu :p

---

### Post by LequidMetal on 2009-11-28
> **krendar said:**
> I would like to add that it is on the Getdeb repository:

[http://www.getdeb.net/updates/#how_to_install]("http://www.getdeb.net/updates/#how_to_install")

After following the instructions all you need to do is:

```

sudo apt-get update
sudo apt-get install songbird
```

I was told that the .deb is a little risky as it has a habit of throwing up unexpected problems so i went for the tar.gz . I got this information from some of the other linux forums .

---

