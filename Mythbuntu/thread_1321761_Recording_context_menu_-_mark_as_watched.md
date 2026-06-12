---
title: "Recording context menu - mark as watched"
date: 2009-11-10
forum: Mythbuntu
---

### Post by buzzlightyear2 on 2009-11-10
I recently upgraded my mythbuntu to 9.10 and mythtv to 0.22 as part of it. Previously I could press the right nav button next to Ok on my Hauppauge remote when a recording is selected, and get a context menu with amongst other things Mark as Watched. Since the upgrade, this menu does not come up, it just toggles the selection between the list view (all Recordings for example) and a specific recording .

Is there any way that I can get this context menu?

Thanks,
Nicki

---

### Post by tgm4883 on 2009-11-10
Press the I key. You will need to map this to a button on your remote

---

### Post by buzzlightyear2 on 2009-11-10
Thanks, I found out how to map the I to a remote key.

> 
vi .mythtv/lircrc

Added a section like this:
begin
    remote = Hauppauge_350
    prog = mythtv
    button = TV
    config = I
    repeat = 0
    delay = 0
end



Now when I press TV on a recording, the context menu comes up. The reason I have to do this is because on my Hauppauge remote the Menu and I is on one key, and I don't know if/how there is a 'shift' function to use the i instead of the Menu.

---

