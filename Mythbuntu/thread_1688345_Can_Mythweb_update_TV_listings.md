---
title: "Can Mythweb update TV listings?"
date: 2011-02-15
forum: Mythbuntu
---

### Post by nhtrader on 2011-02-15
Currently using MythTV 0.24-159 on one PC as FE and BE


I was out of town, and I was excited to access my home MythTV PC.

At my remote location, I had my Win7 laptop and successfully accessed MythTV using [http://myhome.com/mythweb](http://myhome.com/mythweb) (I used my mythweb username and password)

I saw the TV listings and made a few changes to the recording schedule and closed the browser. I was very excited that this worked as expected.

Then the next day I tried to do the same thing but their was a problem. I once again successfully logged in to my MythTV using mythweb, but this time the TV listings grid was blank. There were no TV listings in the grid. The grid bascially displayed no data for all channels.

1. I don't know why this happened and how to prevent it from happening again.
2. Is there a way to use MythWeb to force an update of the TV listings?

---

### Post by azmyth on 2011-02-15
Mythweb grabs the data from the db so mythweb gets new data when mythfilldatabase runs. I'd check your mythfdb is running properly because if it isn't you'll get no listings thus mythweb will display No Data either that or mythweb couldn't connect to the db. In mythweb, click on backend end status and scroll down to the guide data and see how many days it says you have data for. If it says 0, that'll be the problem.

---

### Post by tgm4883 on 2011-02-15
I don't think that can be done from mythweb. You may be able to download putty to your windows machine then SSH into your backend and run mythfilldatabase.

---

### Post by nhtrader on 2011-02-15
azmyth,

So I guess that means that there is no button or option within MythWeb to update TV listings?

As for mythweb's BE status, here's what it shows me...

Last mythfilldatabase run started on 2011-02-13 05:25 and ended on 2011-02-13 05:25. Successful.
There's guide data until 2033-12-16 09:35 (8340 days).

1. Examing BE status response, it appears that ythfilldatabase hasn't run since 2/13/11. I thought that it was suppose to update daily.

2. BTW, in BE-Video Sources, I use "Transmitted Data Guide (EIT)"

3. Is there a parameter that I can change that will run mythfilldatabase more often than once in a while?

---

### Post by tgm4883 on 2011-02-15
> **nhtrader said:**
> azmyth,

So I guess that means that there is no button or option within MythWeb to update TV listings?

As for mythweb's BE status, here's what it shows me...

Last mythfilldatabase run started on 2011-02-13 05:25 and ended on 2011-02-13 05:25. Successful.
There's guide data until 2033-12-16 09:35 (8340 days).

1. Examing BE status response, it appears that ythfilldatabase hasn't run since 2/13/11. I thought that it was suppose to update daily.

2. BTW, in BE-Video Sources, I use "Transmitted Data Guide (EIT)"

3. Is there a parameter that I can change that will run mythfilldatabase more often than once in a while?

Odd, you shouldn't have that many days of guide data. What source do you use for guide data?

---

### Post by nhtrader on 2011-02-15
> **tgm4883 said:**
> Odd, you shouldn't have that many days of guide data. What source do you use for guide data?

As a source, all I can do is reiterate what I stated earlier.

I enter BE and select 3. Video Sources
Then I select a source that I created: Comcast
The listings grabber = "Transmitted Data Guide (EIT)"

That's it. So I think my source is comcast's broadcast stream? 


2. After I setup my router to allow ssh, would I use the  command ...

mythfilldatabase --refresh-today

to manually force an update of the TV listings?

---

### Post by tgm4883 on 2011-02-15
> **nhtrader said:**
> As a source, all I can do is reiterate what I stated earlier.

I enter BE and select 3. Video Sources
Then I select a source that I created: Comcast
The listings grabber = "Transmitted Data Guide (EIT)"

That's it. So I think my source is comcast's broadcast stream? 


Heh, I don't know how I missed that the first time.


> **nhtrader said:**
> 
2. After I setup my router to allow ssh, would I use the  command ...

mythfilldatabase --refresh-today

to manually force an update of the TV listings?

Yep, that would force an update of todays

---

