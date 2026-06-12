---
title: "Intel 3945ABG speed issues finally identified."
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by Starks on 2010-12-23
I spent most of the day bisecting and testing numerous kernels and my work has finally paid off.

I've found 4 candidate commits.

a6866ac93e6cb68091326e80b4fa4619a5957644
1402364162afbaac1b8a74ee21aeb013e817ac7d
7d47618a2ade0cb6d8a0b2597029c383c1662fa0
6db6340c42d027b6364d49fa99d69019aca24de4

iwl3945 definitely broke between 2.6.35-rc2 and -rc3.

---

### Post by vincencollins on 2011-02-08
I am having an issue with the Intel 3945ABG degrading over the course of a day until it won't even connect.  Have you identified a solution?

---

