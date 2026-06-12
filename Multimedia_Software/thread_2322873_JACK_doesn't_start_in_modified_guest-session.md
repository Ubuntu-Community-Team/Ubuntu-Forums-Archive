---
title: "JACK doesn't start in modified guest-session"
date: 2016-05-01
forum: Multimedia Software
---

### Post by Dirk_Hartmann on 2016-05-01
Hello,
I've set up ubuntustudio with a customized guest-account. First I created the special purpose user guest-prefs, as described [here]("https://help.ubuntu.com/community/CustomizeGuestSession").
After this, I created a symbolic link to the home directory of **guest-prefs**:
sudo mkdir /etc/guest-session
sudo ln -s /home/guest-prefs /etc/guest-session/skel

Now the problem:
When I'm locked in as guest-prefs, then I get the jack-server started. When I'm locked in as guest-account, jack does not start. I think, there's something wrong with special permissions. It would be great, if someone could help me.

---

