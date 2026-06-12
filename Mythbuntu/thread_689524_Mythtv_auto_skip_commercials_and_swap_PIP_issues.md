---
title: "Mythtv auto skip commercials and swap PIP issues"
date: 2008-02-06
forum: Mythbuntu
---

### Post by oct on 2008-02-06
I've been using Mythbuntu for a few weeks with good results. But I have to issues. I'm not sure if they are issues or not:

1. Autoskip commercials only skip the first 6 minutes and few seconds of the commercial break. If the break is shorter, works well, but if it's longer, I have to fast forward the rest of the break.

2. When I activate PIP and then swap the windows, the show playing in the PIP (first was the main screen) starts again from the beginning. I'd expect that the playback continues from where I swap the windows.

Is it possible to correct this things? Does anybody else have the same problems?

Thanks for your help

Oct

---

### Post by newlinux on 2008-02-06
1.

Utilities/Setup->Setup->TV Settings->Playback

Scroll through to the commercial skip section and change the max commercial skip to your liking.

2. I don't have this problem, so I'm not sure what it is, but I rarely use PIP

---

### Post by yankcrime on 2008-02-07
newlinux has it right.  the mythtv packaged for ubuntu has the default of 360 seconds (six minutes).

---

### Post by toorima on 2008-02-07
> 2. When I activate PIP and then swap the windows, the show playing in the PIP (first was the main screen) starts again from the beginning. I'd expect that the playback continues from where I swap the windows.

I have the same problem but never use it so haven't looked into it but a solution would be nice.

---

### Post by p$y on 2008-02-08
> **yankcrime said:**
> newlinux has it right.  the mythtv packaged for ubuntu has the default of 360 seconds (six minutes).

hm, I am not able to set this value higher :confused:

---

### Post by oct on 2008-02-08
Newlinux, the parameter you talk about, refers to manually skip commercials. As I read on the documentation, it does not affect autoskip feature. But I have this value to the default of 3600 seconds (not 360), it is, an hour. 

About the PIP issue, I use it in Live TV to jump channels during commercial breaks, keeping an eye to the show I'm watching. But as it  starts playback from the beginning, is it useless for me. I think I'll do some more tests, to see if I find something more...

---

### Post by oct on 2008-03-17
I've been searching the web a little more and found some info about the autoskip max length. As you can read on the ticket [http://www.mythtv.org/pipermail/mythtv-commits/2005-April/005708.html](http://www.mythtv.org/pipermail/mythtv-commits/2005-April/005708.html)  the value of 6 minutes and 35 seconds it is written into the source code and is not changeable. Also, have found another spanish user with the same problem at [http://www.mythtv.org/pipermail/mythtv-commits/2007-September/032753.html](http://www.mythtv.org/pipermail/mythtv-commits/2007-September/032753.html) Does anybody know if there is some way to change this value? Is it possible that newer versions of Mythtv let you modify the max commercial length variable?

About the swap PIP issue, have found a patch that probably solves the problem at [http://svn.mythtv.org/trac/ticket/3175](http://svn.mythtv.org/trac/ticket/3175) I think I will wait unitl the release of Mythbuntu 8.04 to see if that is fixed, unless anybody can tell me how can I use the swappip_fix_seek_value.patch file provided. 

Thank you

Oct

---

