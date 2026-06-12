---
title: "prob with Audio &amp; Video playback"
date: 2008-08-31
forum: Multimedia Software
---

### Post by arunmanoj on 2008-08-31
while trying 2 play any multimedia file (mp3,mpeg...) all the M.M apps throwing the following **error!!!??? *****[COLOR="Red"][SIZE="5"]"Failed to connect stream : invalid argument"[/SIZE][/COLOR]***,then is no playback, i already installed all the codec...pls help me...iam a newbie 2 linux...thanx in advance...1more thing iam using UBUNTU-8.04.1

[[img]http://img512.imageshack.us/img512/7229/errottx0.png[/img]](http://www.imagehosting.com/)

---

### Post by minky311 on 2008-08-31
Go to the Applications->Accessories->Terminal once there try reinstalling totem by typing this
```
sudo apt-get remove totem
```

Then this
```
sudo apt-get install totem
```

---

