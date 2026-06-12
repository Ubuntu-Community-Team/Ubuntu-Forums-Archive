---
title: "Firefox doesn't show some link text"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by ryecomp on 2009-05-04
When accessing some korean [news site]("http://www.pressian.com/article/article.asp?article_num=40090501235809&section=03"), 
link text is always omitted when accessing using firefox. This symptom 
existed for firefox 3.1beta2, ... 3.5beta4 ... 

The site contains many linked texts (colored in blue) that all them are omitted
when rendering in firefox. But if you save the link contents (save Page as ...), 
and browse downloaded link using firefox, it properly show omitted link texts. 

Can you specify what is the problem ? firefox or the site ? 
How to fix it ?? 

Thanks in advance.

---

### Post by cariboo on 2009-05-04
Have you been using the same profile for every version?

---

### Post by ryecomp on 2009-05-04
Same preferences, about:config data. 

No configuration change when upgrading from firefox 3.1beta2 to 3.5beta4. 

When viewing problemabtic page source, 

```
119&#54924; &#45432;&#46041;&#51208;&#51064; 1&#51068; &#49436;&#50872; &#49884;&#45236; &#44275;&#44275;&#50640;&#45716; 2&#51068;&#48512;&#53552; &#49884;&#51089;&#54616;&#45716; &#39;&#54616;&#51060; &#49436;&#50872; &#54168;&#49828;&#54000;&#48156;&#39;&#51012; &#51456;&#48708;&#44032; &#54620;&#52285;&#51060;&#50632;&#45796;. &#44305;&#54868;&#47928; &#49324;&#44144;&#47532;&#51032; <a href="http://search.keywordsconnect.com/?keyword=%B0%A1%B7%CE%B5%EE&article_num=40090501235809&media=pressian" target="_blank" class="adlink">&#44032;&#47196;&#46321;</a>&#50640;&#45716; &#39;&#54616;&#51060; &#49436;&#50872; &#54168;&#49828;&#54000;&#48156;&#39;&#51012; &#50508;&#47532;&#45716; 
```

abc in <a href="..." target="..." class="...">abc</a> .... is omitted from rendering.

---

### Post by ryecomp on 2009-05-17
Self answering. 

This problem is related to text ad (class=adlink), so 
deleting one filter ##*[class^="adlink"] from adblock plus corset filter set, 
fixed problem.

---

