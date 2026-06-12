---
title: "Wireless Authentication"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by shakkydo on 2011-05-27
This is driving me mad. I have been trying to wirelessly connect to my [[COLOR=darkgreen]network[/COLOR]]("http://ubuntugeek.com/forum/index.php/topic,4210.0.html#")  for weeks now. My netgear dongle is fully working. I have installed the  driver using ndiswrapper. I can see my network and signal is excellent;  everything is working perfectly. When I try to connect it thinks about  it but never connects. The password is fine; it works great with other  computers. decided to have a go with wicd, so got rid of the Gnome  network manager and installed wicd. Adaptor and wicd appear to be  working brilliantly EXCEPT I cannot connect. wicd tells me its a bad  password. Password fine because it works brilliantly with every other  device I connect to my network. If I remove security from network, it  tells me it cannot get address, even though it sailed passed that with  no problem when there was security. I have searched the internet for a  solution to this problem time and time again. Lots of people seem to be  having this problem, but no one knows the solution. Is there a solution?  It happens with both Ubuntu 10.04 LTS v1 v2 and Ubuntu 11.04. What the  heck is going on. Any one? Please help. Suicide seems the only other  alternative; (just kidding of course)
This happens with WPA WEP and anything else I try to use
Rob

---

### Post by shakkydo on 2011-05-27
Done it! If you are having the same problems, uninstall completely Gnome network manager or wicd. Then re install it. Worked for me.

---

