---
title: "Wrong generated hex keys?"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by HVJoel on 2009-01-29
Hi,

I use ubuntu 8.10. When I try to connect to networks with a shared key I fail.

This is what happens:
After entering the key I am asked to enter the correct wifi password again. When I chose not to do that and I click show key to see what I've entered before, I see a messed up key, like 2a5b254a681087fc48fc696ff9c0d53db754a40e0a2a55787e29aeba1cdec498.

That was obviously not my network key, cause my real key is only 10 characters long.

Then I was at a friends place, he had a WEP encryption at his network, same story it wouldn't connect. Then I took his laptop with windows7 beta installed. When you press show key in windows7, you also get to see a messed up key like the one above. However that one is different from the key that ubuntu generates.

After entering the key that has windows7 generated I connected to the network without any problems. Now I'm at home and have to use wifi, but I don't have a windows7 laptop available to generate a key.

Does anyone know what to do? Or can anyone tell me what settings to use? I attached a screen shot from my network settings.

---

### Post by icheyne on 2009-01-29
The screenshot you included has a "Random" button underneath the shared key text box. Did you click it by accident?

---

### Post by HVJoel on 2009-01-29
> The screenshot you included has a "Random" button underneath the shared key text box. Did you click it by accident? 
Nope, there is also a save button. But that one is invisible at the screenshot. I installed wicd. With wicd I can connect without problems. I think it's some kind of bug in the wifi manager which comes default with ubuntu.

---

