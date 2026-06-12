---
title: "kdenlive crashes during render"
date: 2012-09-04
forum: Multimedia Software
---

### Post by mattgeb84 on 2012-09-04
i have kdenlive 9.2 running xubuntu 12.04 , i made a video but when i go to render it, the render dialog box stops making any progress around the halfway point, it doesn;t seem to matter what file type i render too ?
help would be appreciated

---

### Post by shantiq on 2012-10-10
hi Matt not sure if you have sorted this but just had a go and realized the one in repos not doing the business so maybe try this [i had to do this myself]


```
sudo apt-get remove --purge kdenlive
```


and then


> sudo add-apt-repository ppa:sunab/kdenlive-release && sudo apt-get update && sudo apt-get install kdenlive



see if it cures it for you

---

