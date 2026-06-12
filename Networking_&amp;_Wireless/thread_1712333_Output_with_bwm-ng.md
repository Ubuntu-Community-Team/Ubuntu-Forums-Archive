---
title: "Output with bwm-ng"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by romeroc24 on 2011-03-22
Sorry my English not so good.

I used bwm-ng (bandwidth monitor new generation), like follows:

bwm-ng -o csv -c 4 -I eth0

The options means, an csv format output, 1 count, and only monitor interface eth0.

Output result:

1300818021;eth0;1215.00;43142.00;44357.00;43142;1215;18.00;32.00;50.00;32;18;0.00;0.00;0;0
1300818021;total;1215.00;43142.00;44357.00;43142;1215;18.00;32.00;50.00;32;18;0.00;0.00;0;0

I only want the first row, i.e. only the ehternet data, no the total data. How can I do it?

---

