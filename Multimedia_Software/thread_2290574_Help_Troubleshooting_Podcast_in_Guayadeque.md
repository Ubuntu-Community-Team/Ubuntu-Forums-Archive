---
title: "Help Troubleshooting Podcast in Guayadeque"
date: 2015-08-13
forum: Multimedia Software
---

### Post by lambdafox on 2015-08-13
I have set up two podasts in Guayadeque.  Both are set to download all and allow delete of old items.

The first:
NPR's Morning Edition
RSS Feed:
[http://www.npr.org/rss/rss.php?id=3](http://www.npr.org/rss/rss.php?id=3)

The second:
Science Friday
RSS Feed
[http://www.sciencefriday.com/audio/scifriaudio.xml](http://www.sciencefriday.com/audio/scifriaudio.xml)

Science Friday shows every podcast in the list as it should.

Yesterday, Morning Edition showed only the first item in the feed.  Today it shows nothing at all.

Is this sort of thing common and will resolve itself?

Or, do I need to report a bug to someone (NPR or Guayadeque?)

Do I maybe need to change some configuration item in Guayadeque?

Other ideas?

---

### Post by tgalati4 on 2015-08-13
Well, I use *gpodder* and the Morning Edition showed no new episodes.  So that link may be broken.  The Science Friday link showed 61 episodes.  I was able to download and listen to the oldest episode on STEM and Planet Rotation.  That link appears to be working.  You might want to send an email to someone at NPR.

When I perform a *wget* on the Morning Edition RSS feed, I get what seems to be a valid RSS file: (showing only a portion)

> <?xml version="1.0" encoding="UTF-8"?>
<rss xmlns:npr="http://www.npr.org/rss/" xmlns:nprml="http://api.npr.org/nprml" xmlns:itunes="http://www.itunes.com/dtds/podcast-1.0.dtd" xmlns:content="http
://purl.org/rss/1.0/modules/content/" xmlns:dc="http://purl.org/dc/elements/1.1/" version="2.0">
  <channel>
    <title>Morning Edition : NPR</title>
    <link>http://www.npr.org/templates/story/story.php?storyId=3</link>
    <description>Morning Edition gives its audience news, analysis, commentary, and coverage of arts and sports. Stories are told through conversation as wel
l as full reports. It's up-to-the-minute news that prepares listeners for the day ahead.</description>
    <language>en</language>
    <copyright>Copyright 2015 NPR - For Personal Use Only</copyright>
    <generator>NPR API RSS Generator 0.94</generator>
    <lastBuildDate>Thu, 13 Aug 2015 07:11:00 -0400</lastBuildDate>
    <image>
      <url>http://media.npr.org/images/podcasts/primary/npr_generic_image_300.jpg?s=200</url>
      <title>Morning Edition</title>
      <link>http://www.npr.org/templates/story/story.php?storyId=3</link>
    </image>
    <item>
      <title>Norway 'Slow TV' Event To Broadcast Reindeer Migration</title>
      <description>The event on NRK, Norway's national broadcaster, will only last a week. The project manager says anything more would be "too slow &#8212; even f
or slow TV."</description>
      <pubDate>Thu, 13 Aug 2015 07:11:00 -0400</pubDate>
.
.
.


The formatting of the file or other error is not obvious to me, yet.  And, no errors when running *gpodder* in a terminal.  Try running *guayadeque* in a terminal with the --debug switch and see if any errors come up.  The work-around is to *wget* the RSS file and then *wget* the individual podcast files.

---

### Post by lambdafox on 2015-08-13
> **tgalati4 said:**
> Well, I use *gpodder* and the Morning Edition showed no new episodes.  So that link may be broken.  ,,,You might want to send an email to someone at NPR. ...

interesting to know that at least one other reader is having the same problem.

Thank you!  will do that.

---

### Post by tgalati4 on 2015-08-13
The RSS feed points to a webpage for a story about Reindeer Migration:  [http://www.npr.org/2015/08/13/432036083/norway-slow-tv-event-to-broadcast-reindeer-migration?utm_medium=RSS&amp;utm_campaign=morningedition](http://www.npr.org/2015/08/13/432036083/norway-slow-tv-event-to-broadcast-reindeer-migration?utm_medium=RSS&amp;utm_campaign=morningedition)

That page has an embedded Javascript audio player with a download link:  [http://pd.npr.org/anon.npr-mp3/npr/me/2015/08/20150813_me_hr2_return_rm_-_alyssa.mp3?dl=1](http://pd.npr.org/anon.npr-mp3/npr/me/2015/08/20150813_me_hr2_return_rm_-_alyssa.mp3?dl=1)

Because of the two-step, the RSS feed does not list the episodes directly.

---

