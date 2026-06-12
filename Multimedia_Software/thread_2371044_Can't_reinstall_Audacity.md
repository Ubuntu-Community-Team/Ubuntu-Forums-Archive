---
title: "Can't reinstall Audacity"
date: 2017-09-10
forum: Multimedia Software
---

### Post by Dai Griffiths on 2017-09-10
I had a problem with Audacity: when I went to launch it, it told me that it was already running.

I decided to reinstall, which I have done before when I have had problems with Audacity crashing. 

I had installed Audacity through the 'Ubuntu Software' application, so I went there and clicked remove. It did something, because the icon disappeared, but 'Ubuntu Software' still thinks that it is installed. I still get the 'Remove' button, however often I click it, and no 'install' button.

Any suggestions?

Thanks

dai

---

### Post by RobGoss on 2017-09-10
After you removed Audacity try restarting your machine and then see if the program is still detected, sometimes a restart is needed to refresh the machine

---

### Post by Yellow Pasque on 2017-09-10
CLI time:
```
sudo apt-get purge audacity
```

---

