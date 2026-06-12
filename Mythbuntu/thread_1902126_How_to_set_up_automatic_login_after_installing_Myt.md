---
title: "How to set up automatic login after installing Mythbuntu 11.10"
date: 2011-12-30
forum: Mythbuntu
---

### Post by PatrickD-52761 on 2011-12-30
Hello everyone,

When I installed Mythbuntu 11.10, I didn't need/want to have it automatically log me in. But, now I decided to move the computer into another room, and use it as a DVR only setup. So, I don't want to have a keyboard/mouse (if possible). The problem I have is that I can't configure Mythbuntu to automatically log me in.

How do I go about this? I edited the lightdm.conf file with the following

```

automatic-login=myuser
session-greeter=mythbuntu-lightdm-gtk-greeter

```

I found this listed at [http://askubuntu.com/questions/65957/how-do-i-enable-automatic-login-in-mythbuntu-11-10]("http://askubuntu.com/questions/65957/how-do-i-enable-automatic-login-in-mythbuntu-11-10"). Now, when I boot up, I get a black screen (no login, and mythtv doesn't open). So I'm not sure what I needed to do afterwards.

Any help is greatly appreciated.

Have a great day:)
Patrick.

---

### Post by PatrickD-52761 on 2011-12-30
Ok, it appears that I wasted my (and anyone else who viewed this) time.

On [http://ubuntuforums.org/showpost.php?p=11095806&postcount=28]("http://ubuntuforums.org/showpost.php?p=11095806&postcount=28"), I found the solution.  I just tried it, and it works perfectly. Of course that's with a keyboard and mouse still attached (I may leave them connected in case I have to update).

Have a great day:)
Patrick.

---

