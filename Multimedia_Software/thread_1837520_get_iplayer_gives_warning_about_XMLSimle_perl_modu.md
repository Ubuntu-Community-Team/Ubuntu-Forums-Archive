---
title: "get_iplayer gives warning about XML::Simle perl module and fails to record"
date: 2011-09-01
forum: Multimedia Software
---

### Post by chamira on 2011-09-01
I am a noob to Ubuntu hacking by the way although  I have been a happy user for a couple of years.

I think I have the latest version of the player installed. I followed this advice to install the most up-to-date version: [http://ubuntuforums.org/showpost.php?p=10916662&postcount=13](http://ubuntuforums.org/showpost.php?p=10916662&postcount=13)

I am typing this command: 
get_iplayer --force it --pid=b00ysny1


I am getting the following error:

WARNING: Please download and run latest installer or install the XML::Simple perl module to use the Series and Brand pid parsing functionality
INFO: Trying pid: b00ysny1 using type: tv
INFO Trying to stream pid using type tv
INFO: pid not found in tv cache
INFO: Checking existence of default version
INFO: No specified modes (flashhigh,flashstd,flashnormal) available for this programme with version 'default' (try using --modes=)
ERROR: Failed to record 'The Killing - Episode 8 (b00ysny1)'

How do I install the XML::Simple perl module?

---

### Post by shantiq on 2011-09-02
code is wrong chamira ....   the pid looks like this it is the address you find in the url on the BBC page or you can use --get and the number


MAIN CODE REQUIRED FOR TV
==================

```
get-iplayer --vmode=flashhd --pid=http://bbc.co.uk/programmes/p00k30c4

```

or    run    ```
get-iplayer
```   and you will find the number of the program then run

```
get-iplayer --vmode=flashhigh --get (the number you find for the program you want)
```


you can also add     ```
--subtitles
```   if you want those

if you run     ```
--test 
```  it will show you the  mode options for a given program 

THEY ARE:  RecoRding modes: 

```
iphone,flashhd,flashvhigh,flashhigh,flashstd,flashnormal,flashlow,n95_wifi,flashaac,flashaudio,realaudio,wma
```



AND FOR RADIO
============

example


```
get_iplayer --mode=flashaac1 --pid=http://www.bbc.co.uk/iplayer/episode/p006rpsn/Assignment_Love_and_Morals_in_Mangalore/ 
```



also do not know if you are in the UK    it only works in the UK unless you do a[** proxy change**]("http://bbs.scoobynet.com/computer-related-34/658352-how-to-get-bbc-iplayer-to-work-outside-uk.html")

**All the options are [HERE]("http://www.digipedia.pl/man/doc/view/get-iplayer.1/")**


best of luck    shan



=====================================================

[B]SUMMARY
==========[/B]


1. NEED TO BE IN uk or using a UK proxy address
2. run  ```
 get-iplayer
```   then see number of your program  **OR**   find pid from [**bbc iplayer page**]("http://www.bbc.co.uk/iplayer/")


3.   Use info above

---

