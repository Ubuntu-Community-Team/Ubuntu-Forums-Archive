---
title: "5 Tips To Boost Page Speed"
date: 2014-08-27
forum: Multimedia Software
---

### Post by sumon2 on 2014-08-27
[h=2]5 Tips To Boost Page Speed[/h]  While the above information is interesting and good to know, the real question is, how can you speed up your site today? Below are a few tips to help you do just that.
  **1. Optimize Your Database**

  Most sites use databases to store information. If you have an e-commerce store, blog, news site, or any type of dynamic functionality like internal search, then you are using a database. However, your database can impact your page speed.
  Adding an index is one of the best ways to optimize your database for page speed improvements. Doing so will help your database find information faster. Instead of having to scan millions of records, your database can rely on an index to narrow down the data to a few hundred. This helps the data get returned to the page much faster.
  For example, recently I was working on a site where the most popular pages were loading very slowly, taking between two to ten seconds each.
  The problem was buried in the database — the table that stored the requested data didn’t have an index on it. After adding the index, the average page load time was reduced from the 2- to 10-second range to less than 1 second.
  As you can see in the chart below, some load times were north of ten seconds — and, as I mentioned earlier, *nobody* is going to wait that long for a page to load. (Note that the page load times are measured in seconds — the lower the number, the faster the page loaded.)
  [IMG]file:///C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\msohtml1\02\clip_image002.jpg[/IMG]
  Page Speed Comparison Chart
  **2. Ditch Your Tracking Codes, Video Embeds & Share Buttons**
  Yep. You heard me right. You don’t need five different analytics programs. While tracking codes are vital for analyzing user behavior onsite, marketers should review each analytics program and determine which is necessary.
  Remember, *simplicity is key*. Every time you add another tracking code to your page, it slows it down. For tracking codes you do include, be sure to put it at the bottom of the page. That way, the page can be displayed to the user even if the code hasn’t finished loading yet.
  Also, limit the use of video embeds. Why? Video is a great way to build consumer engagement and create a better user experience; however, most video embeds (including YouTube) use [iFrames]("http://www.w3schools.com/tags/tag_iframe.asp") to display the video.
  iFrames place a real drag on page load times because they are essentially causing you to load a whole separate page within your main page.
  [CENTER][CENTER][IMG]file:///C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\msohtml1\02\clip_image004.jpg[/IMG][/CENTER][/CENTER]  The same goes for share buttons. Marketers should use share buttons to increase referral traffic and reach new consumers. However, most share buttons are javascript-based, and all the javascript does is generate an iFrame on the page.
  Try limiting the number of share buttons on each page. This will help prioritize the marketing benefits rather than the negative impact to page speed.
  **Balance Page Speed With Rankings & Traffic**
  In each of the above cases, the brand manager needs to balance the risk of a slower page speed with the benefits of each initiative. The best way to make this decision is by testing the change and analyzing its effect on rankings and traffic against your KPIs.
  For instance, many sites would prefer an increase in traffic due to share buttons and are comfortable with a decrease in rankings.
  Bottom line: Multiple videos or share buttons on a page can dramatically slow down load time.  It’s okay to use tracking codes, embed videos, and include share buttons, but be selective.
  **3. Use Caching When Available**
  When you visit a web page for the first time, your browser needs to request *all* the images, text, scripts, etc. from the website’s server. They are stored in your browser’s cache so that when you visit other pages on the site, you only need to download the parts of it that are unique. For example, the site’s logo will likely be the same on every page, so that is an image the browser can load from its cache quickly.
  Up until the last year or two, browser caching capabilities were pretty limited. But once HTML5 came on the scene, it received some major updates.
  For example, [Local Storage]("http://diveintohtml5.info/storage.html") allows you to store megabits of data using the browser instead of requiring it to be stored in your server’s database.
  Alternatively, [Application Cache]("http://www.html5rocks.com/en/tutorials/appcache/beginner/") lets you write fully-functional web applications that can run offline. The benefits of these two caching mechanisms are:

  
[LIST]
[*]**Speed**: They      allow you to access resources from your local computer so you don’t have      to wait for the server to provide them.
[*]**Cost Savings**:      As you increase the use of local storage, your server use will decrease.      That means you’ll be paying for less bandwidth and server usage.
[*]**Offline Browsing**:      Your users won’t have to worry about your app not working when their Wi-Fi      goes down; their phone enters a dead zone, or you need to take the site      down briefly for maintenance.
[/LIST]
  Also, if you use WordPress, you are in luck if there are many great caching plug-ins available to help speed-up a site. My favorite right now is [Quick Cache]("https://wordpress.org/plugins/quick-cache/").
  [CENTER][CENTER][IMG]file:///C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\msohtml1\02\clip_image006.jpg[/IMG][/CENTER][/CENTER]  **4. Content Delivery Networks**
  Imagine that your website’s server is located physically in Texas. Your site should load quickly for residents there because its data need only travel a short distance  from the server to their computer.
  Now, imagine a user in Paris wants to visit your site. The web page data must travel from Texas to France, stopping at multiple routers along the way. This delay, or “latency,” is added to every single byte of data that is transferred — every image, every video, every javascript file, every CSS file, etc.
  Wouldn’t it be great if a copy of your page could exist in a server both in Paris and in Texas? This is exactly what a content delivery network (CDN) does.
  A CDN has servers all over the world, and they’ll store a copy of your website on those servers. This way, no matter where a visitor is, they’ll have access to content resident on a nearby server.
  [IMG]file:///C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\msohtml1\02\clip_image007.gif[/IMG]
  Content Distribution Network
  The good news is that there are plenty of CDNs out there; however, most are paid services. If you use Amazon for hosting, you can tap into their [CloudFront]("http://aws.amazon.com/cloudfront/") service for CDN capabilities. If you’re a Rackspace customer, you’ll be happy to know that [they partnered with Akamai]("http://www.rackspace.com/information/mediacenter/announcements/akamai/") to offer their customers CDN offerings.
  But you don’t *have* to pay for a CDN. Surprise, surprise, Google is offering a free CDN called [PageSpeed Service]("https://developers.google.com/speed/pagespeed/service?csw=1"). In true Google fashion, they’re giving it away for free *for a while*. Then once you’re hooked, they’ll charge for it. That said, pricing will likely be competitive, and you’ll always have the option of switching to another provider down the road.
  **5. The Most Important Page Speed Tool**
  Within Google Webmaster Tools you now have access to “[PageSpeed Insights]("http://developers.google.com/speed/pagespeed/insights/").” This tool analyzes a given URL’s page load speed, and gives you tips on how to make improvements.
  It is particularly valuable because Google uses a similar speed analysis as a factor in your rankings. Using this tool will allow you to see what Google sees. And if you’re smart, you might want to run it for competitors, and see how you stack up!
  [IMG]file:///C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\msohtml1\02\clip_image008.jpg[/IMG]
  Image used with permission of Shutterstock.com
  [h=2]Do It For Your Users[/h]  Again, nobody is going to wait around for your site to load. Today, speed rules. And now Google is paying a lot more attention to it than ever before. So take action, and improve your page speed now. Do it for your users!
  Remember, you will never go wrong by making your site faster — traffic will never decrease, sales will never drop and engagement will never fall off. We all love speed, and if your site is blazing fast, we will all love you!
  *How has page speed affected your rankings? Got any page-speed boosting tips and tricks? Please share them here.*
   
  [CENTER][CENTER]  [HR][/HR]  [/CENTER][/CENTER]
  *Some opinions expressed in this article may be those of a guest author and not necessarily **Search**Engine**Land**. Staff authors are listed .*

---

### Post by TheFu on 2014-08-27
Another page speed vendor is [http://zoompf.com/](http://zoompf.com/) - a free scan is possible.
This is from [Billy Hoffman]("https://en.wikipedia.org/wiki/Billy_Hoffman"), if that matters.

If you get a chance, watch a talk that Billy gives (search youtube) - always full of technical data AND funny.  I saw him rip apart a few select, well-know, websites during a server performance talk a few years ago. It was sad how poorly those were written - most had more than 30 outside website/js/css/tracking links - extremely slow.

---

