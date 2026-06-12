---
title: "stderr output of cdparanoia for progress bar"
date: 2010-10-30
forum: Multimedia Software
---

### Post by atarax42 on 2010-10-30
I am currently working on a CD ripper front end for cdparanoia. My problem is to find a way to get the current sector of the CD that is being ripped to update the respective progress bar of the application's gui. At the moment I use a python method like this:

```
    def button1_clicked(self, widget):
        task = self.actRip(11)
        gobject.idle_add(task.next)
            
    def actRip(self, n):
        cmd = ("cdparanoia", "-e", "-Z", "-B", "-v", "-d", "/dev/scd0", str(n), "/home/atarax/Desktop/Rip/ripper03/wav")
        ripping = subprocess.Popen(cmd, stderr=subprocess.PIPE)
        log = open("/home/atarax/Desktop/Rip/ripper03/log", "w")
        for line in ripping.stderr:
            if "[read]" in line:
                low = 187762512.0  # offset value found in log file
                high = 197609160.0  # finish value found in log file
                position = float(line[(line.rfind(" ") + 1):-1])
                self.entry1.set_text(str(position))
                fraction = (position - low) / (high - low)
                self.progressbar1.set_fraction(fraction)
                percent = int(fraction * 100)
                self.progressbar1.set_text("Track " + str(n) + ": " + str(percent) + " %")
                log.write(line)
            yield True
        yield False
```
        
This is just a reduced snippet as an example of the procedure. The output of ripping.stderr returns lines that contain completely different values as the track info created by cdparanoia -Q, like this:
##: 0 [read] @ 187984776
I cannot find an obvious relationship between those values of ripping.stderr and the sector values. Even the values of [read] and [wrote] are not congruent. There's also a difference between the return values when the paranoia error check is set or not. So it seems impossible to calculate the offset and finish value in advance. When ripping the CD via command line I get the rich bargraph ([http://www.xiph.org/paranoia/faq.html#progbar](http://www.xiph.org/paranoia/faq.html#progbar)) that seems to be pretty useful, but how can I redirect this output to my script, while ripping.stderr offers much poorer information?

Thank you for your assistance.

---

