---
title: "Nvidia shield remote"
date: 2021-01-09
forum: Multimedia Software
---

### Post by whzzz282 on 2021-01-09
Has anyone had success with using the Nvidia Shield remote on ubuntu?
I have successfully paired it (bluetooth), and the arrow keys work, as well as the audio volume slider. I think the back and Home buttons are working (xev shows key press events), but the Select button does not work.

When I run irw, i can see key presses for the arrow keys, but nothing appears for the other three buttons.
When i run xev, i get KeyPress events for the back, home and arrow buttons, but nothing for the "Enter" button.

I confirmed the remote is not broken by re-pairing it to my Shield and confirmed the select button does work.

Has anyone managed to get the shield remote working properly?
Or does anyone have any suggestions on how i might troubleshoot this?

Cheers.

---

### Post by whzzz282 on 2021-01-10
More testing:
- Now tested with both a 2017 and 2019 remote. Both have the same issues. I think Ubuntu is seeing them as a keyboard, and cant handle/has no mapping for the select key. The device does not appear under /dev/inputs. I only can see keyboard and mouse.
- Tested both the 2017 and 2019 remotes in windows 10. The 2017 remote would pair, but not start (error code 10). The 2019 model paired and worked successfully, including the select button.

---

### Post by droyellis on 2021-04-15
hi im also having the same issue with a 2019 shield tv remote, id really like to know how to fix it

---

