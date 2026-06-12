---
title: "Xorg and HDMI AUDIO not working with custom modelines"
date: 2009-02-12
forum: Mythbuntu
---

### Post by rodercot on 2009-02-12
FYI all,

 Thought I would post this little solution in case you get stuck.

 IT seems if you use custom modelines in your xorg file and you use the option

 Option "UseEDID" " "False" 

 This will stop X from reading info from the TV BUT it will also KILL your audio from HDMI. 

 The solution here is to use 

 Option "ModeValidation" "NoEdidModes"

 Regards,

 Dave

---

