---
title: "realtek wireless 10.10"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by tomberet on 2011-02-12
i have a out of the box ubuntu 10.10 desktop edition on a inspiron mini 1018, with a realtek wireless driver, which for some reason does not work. the link to a download is [COLOR="RoyalBlue"][here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE")[/COLOR](click on here) i am a extremly new so i would appreciate exact directions assuming the tar.gz was on my desktop

---

### Post by Spyderkid on 2011-02-12
1) download from here... [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

2)go to applications > accesories > Terminal and type in this...
```

sudo apt-get install build-essential

```

3)folow the read me instructions:
type these into terminal (one at a time)

```

sudo su
make
make install
sudo reboot

```

---

