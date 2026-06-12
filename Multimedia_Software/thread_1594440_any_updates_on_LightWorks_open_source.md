---
title: "any updates on LightWorks open source?"
date: 2010-10-12
forum: Multimedia Software
---

### Post by Dan Johns on 2010-10-12
I am curious about the LightWorks open source release. I read somewhere that it is in private beta, but I haven't received any updates since I subscribed to the mailing list. 

Just wondering if anyone has any info on it, or if anyone is a part of the private beta testing.

---

### Post by shaunthesheep on 2011-04-02
> **Dan Johns said:**
> I am curious about the LightWorks open source  release. I read somewhere that it is in private beta, but I haven't  received any updates since I subscribed to the mailing list. 

Just wondering if anyone has any info on it, or if anyone is a part of the private beta testing.

Lightworks  video editor is not a private beta, it is a public beta for Windows  only at the moment (it began life 20 years ago as a high end Windows  editor so this is understandable) but work on Linux and Mac versions is  scheduled to begin in quarters 3 and 4 of 2011. The release of the  source code is scheduled for Summer 2011. However, there are some  technical and legal issues which have to be sorted before it can be  released. At the moment, the developers are literally going through  hundreds of thousands pf pages of 20 year old code line by line--a huge  task--to check that there are no intellectual property issues before  they can release it. 

And there are some challenging technical issues too. A [discussion has already begun]("http://www.lightworksbeta.com/index.php?option=com_kunena&func=view&catid=10&id=189&Itemid=269") on the Lightworks beta forum about how a Windows programme can best be ported to Linux and Mac.

I  have been intensively beta (and alpha) testing the Windows version  since November 2010 when it was first released. Essentially, the quicker  the Windows version becomes stable, the sooner work can begin on the  Linux and Mac versions. That is one of the reasons I have been beta  testing the Windows version.

Some historical background.  Lightworks has had several owners over the last 20 years and up to last  November (2010) it was available only as an expensive turnkey system  sold to professional film studios and video editing shops. I don't think  it was even available for individual consumers to purchase (I imagine  the cost would have been too prohibitive). By turnkey, I mean that the  editor came with purpose built hardware as a complete solution. The term  turnkey comes from the construction industry where homes are built,  furnished and decorated so that all the new owner has to do is literally  "turn the key".

However, [EditShare]("http://www.editshare.com/"),  its current owners, announced last year that it was going to release an  open source version of Lightworks. You can get an idea what Editshare  does as a business from this [video interview]("http://www.macvideo.tv/editing/interviews/index.cfm?articleid=110861")  with its Boston, Massachusetts based CEO Andy Liebman. Essentially,  the company specialises in offering Avid and FCP editors a means of  sharing projects and working on them collaboratively. EditShare is also  all about interoperability between editors.

Twenty years ago,  there were very few of the video formats (container/codec combinations)  that exist today. Lightworks was mainly used for film editing and a very  few industry standard video formats. So, a big part of the current beta  testing is:

a) getting Lightworks to function on a multiplicity  of hardware combinations that its new users will have (instead of just  one purpose built hardware system) 

and

b) introducing  Lightworks support for the many video formats (professional and  consumer) that have emerged in the past 20 years. Every new camera seems  to introduce a new codec these days so this is a big challenge.  Lightworks at the moment supports only a [few container/codec combinations]("http://www.lightworksbeta.com/index.php?option=com_kunena&func=view&catid=19&id=1277&Itemid=269"). But codec support is increasing all the time with each new beta release. 

One  problem is that some codecs are proprietary and EditShare cannot just  provide these free of charge with the free editor  because it has to pay  fees to use them. Proprietary codecs are not licensed to users but to  the application. So, even if you already have a proprietary codec on  your computer from another commercial editor, it does not follow that it  can be legally used with another free application like Lightworks. This  is something that is beyond Editshare's control and is a matter of  intellectual property licensing. Editshare, as a supplier of a free high end  editor, has to tread carefully as far as intellectual property is  concerned--it could be a target of law suits if it did not.

The  Lightworks developers are working on open source alternative codecs, but  some professional editing shops may need to purchase a proprietary  codec from the Lightworks store (when it opens).

For Ubuntu users  who duel boot with Windows, there is a need for more beta testers of  the Windows version. This would expedite its stable development and help  bring forward the date when work can begin on the Linux version. Beta  testers will also be able to get to know how the editor works so that  when the Linux version is developed they will already be familiar with  its UI. It is a little different from Avid and FCP and although it is  quite intuitive, it takes a little while to learn its ways. The  Lightworks forum is one of the most courteous and helpful I have come  across and the moderators and developers react swiftly and efficiently  to users' questions.

Because of its professional industry  background, some of the newer HD consumer video formats like AVCHD are  not yet fully supported in all container/codec combinations. For example  at the time of writing, the h.264 codec/mp4 container combination is  supported but not the h.264/mts combination. So, re-wrapping may be  necessary until support is introduced. 

And support for smooth playback of long GOP formats like AVCHD is on the to do list or Lightworks [roadmap]("http://lightworksbeta.com/index.php?option=com_content&view=article&id=112&Itemid=246") as it is more properly known. So, transcoding may be necessary at present.

Don't expect Lightworks to work with all video formats just yet. It is in development.

---

### Post by Ubuntiac on 2011-04-08
Thanks for sharing this.

It's great to know that there's still life in this project. Out of curiosity, how rapidly are they iterating new releases? Have they put any out since the original public alpha/beta release?

---

