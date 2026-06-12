---
title: "S Video Out Doesn't Work"
date: 2009-04-10
forum: Multimedia Software
---

### Post by soccerweapon on 2009-04-10
Hello out there...I have a Compaq Presario R3000 laptop with the  Mobility Radeon 9100 IGP and I am trying to use the S Video to the TV so I can watch some of my movies on the TV screen.  I am new to Linux and Ubuntu so if anyone could give me some advice I would really appreciate it.

---

### Post by bgerlich on 2009-04-10
Try:
```

sudo xrandr --addmode s-video 800x600
sudo xrandr --output s-video --mode 800x600

```

---

### Post by soccerweapon on 2009-04-13
i tried that and gives me xrandr: cannot find output "s-video".
might sound like a stupid question but do i need to have the s-video cable from the tv connected when doing this???

---

### Post by bgerlich on 2009-04-14
If you are using ATI proprietary driver setup the S-video output in Catalyst control center instead of using xrandr.

---

### Post by soccerweapon on 2009-04-14
bgelich i thank you for trying to help me out, but I am a noob when it comes to running Ubuntu/Linux. Just recently ditched Windows.  So if you could explain to me what you just said like I don't have a clue (which I don't), I would greatly appreciate it.

---

