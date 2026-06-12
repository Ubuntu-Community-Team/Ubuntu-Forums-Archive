---
title: "haup pvr-150 no longer recording"
date: 2009-02-05
forum: Multimedia Software
---

### Post by OmahaVike on 2009-02-05
(Hardy)

Thanks for taking the time to open up my request for help.

I'm hoping for assistance on diagnosing a problem.  My Hauppage pvr-150 used to be able to record (input 2, composite) by using 'cat /dev/video0 > filename.mpg'.  This is no longer the case.  It now creates a file with 0 bytes.

I have also confirmed that MythTV is producing the same output problems on the coaxial input (input 0), so the card IS producing output -- my monitor is still working as I type this -- but IS NOT taking input.  The last successful recording was made (scheduled, not manual) on Jan 23rd.

Where would I begin to look in my system for drivers that may have changed through synaptic?  Are there any other spots I should look to investigate change that may have affected the card?

Thanks to any and all guidance you might provide.

---

### Post by punx45 on 2009-02-06
mythtv is probably switching the card to the coax input.   

see here on how to use ivtv-ctl or its newer counterpart for newer versions of ivtv.   try using it to set the input to composite, then cat-ing the tuner again.

[http://ivtvdriver.org/index.php/Ivtvctl](http://ivtvdriver.org/index.php/Ivtvctl)

---

### Post by OmahaVike on 2009-02-07
thanks for the quick turnaround.  

as i stated in my original post, ABSOLUTELY NO INPUT IS BEING RECOGNIZED.  catting /dev/video0 results in 0 length file *and* mythtv is no longer recording off coax(0 length file too), and composite is not recording as well.

does anyone know how to check the "history" of driver updates?  that's the only thing i can suspect as being the problem.  it used to work (as of the middle of january) and now it doesn't.

thanks!

---

### Post by punx45 on 2009-02-08
aptitude show ivtv-modules

should show what version you have installed.

or you can check the package manager if you prefer GUI.   either should also allow you to force an older version.

---

