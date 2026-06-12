---
title: "title bar off screen"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by tronica on 2006-08-08
i got dual monitors going with my nvidia 5200, but when i maximize window the title bar goes off screen. could this be a issue with what i added to my xorg.conf

> Option      "TwinView"
	Option      "SecondMonitorHorizSync" "30.0 - 97.0"
	Option      "SecondMonitorVertRefresh" "50.0 - 180.0"
	Option      "MetaModes" "1400x1050, 1400x1050"

thanks

---

### Post by tronica on 2006-08-08
nevermind i got it, i just commented out these

> Option "TwinView"
#Option "SecondMonitorHorizSync" "30.0 - 97.0"
#Option "SecondMonitorVertRefresh" "50.0 - 180.0"
#Option "MetaModes" "1400x1050, 1400x1050" 

---

