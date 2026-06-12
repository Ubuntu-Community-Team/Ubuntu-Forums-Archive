---
title: "Installing Ardour"
date: 2008-03-01
forum: Multimedia Production
---

### Post by foxteria on 2008-03-01
Greetings, I'm a newbie here, and I have a basic question.
I've installed Ubuntu 7.10 on a computer and it's working fine. What is the easiest way to put Ardour on that computer. (It's not on line)
Thanks

---

### Post by Stochastic on 2008-03-02
I'd say the best way would be to hook it up online for a second (if that's possible) and (though you may need to add online repositories first) do: ```
sudo apt-get install ardour
```

There is also the option of downloading the Ubuntu Studio DVD and using it as a repository (can be selected through synaptic).  Once you've done that, then just do that above command.

But if you can't do either of those, then you're going to face a bit more of a challenge.  You will need to get online to download Ardour (try to find a .deb file) and all it's dependencies.  Now that last bit is the tricky part.  See, Ardour can't even install properly without the adequate libraries and audio drivers installed first.  For a complete listing, take a look at this page (though if you've found a .deb file then you can skip the 'Required Tools' section) [http://www.ardour.org/building](http://www.ardour.org/building)

now if you're not overwhelmed yet, then you're not a true newbie;)

---

### Post by Drunky on 2008-03-02
Be sure JACK is working also.

---

### Post by Stochastic on 2008-03-02
JACK is one of the dependencies of ardour.  If you're installing from any repo (online or UbieStudioDVD)  then  apt-get will take care of installing JACK.

---

### Post by foxteria on 2008-03-02
Thanks folks, I'm up and running.

---

