---
title: "Creating a video surveillance system with Motion"
date: 2012-01-17
forum: Multimedia Software
---

### Post by ionas.alex on 2012-01-17
Hello guys, i am relatively new in the ubuntu playground, and that's why i need your help. I have a project for my school teacher, i have to create a video surveillance system, basically, get the camera built inside a laptop working, and one more camera attached via USB, with motion. Now i installed motion, configured some stuff in the motion.conf file, and if i access the localhost i can see the webcam working, but only the one built-in the laptop. As i understood if you have multiple cameras you need separate threads.conf file, now how do i edit that? if i try to access the thread1.conf i get "bash: /etc/motion/thread1.conf: Permission denied, and yes i am logged as root. 

And one more thing, is it possible to make motion broadcast over the internet, like assign an IP address so i can access them from my school basically, because it only works in localhost.

Thanks, and please help.

---

### Post by nkbatsi on 2012-01-17
Did you try editing the file through a terminal? Always use sudo even if you are root. You might want to use midnight commander (mc), which runs through a terminal and makes your life easier!

---

