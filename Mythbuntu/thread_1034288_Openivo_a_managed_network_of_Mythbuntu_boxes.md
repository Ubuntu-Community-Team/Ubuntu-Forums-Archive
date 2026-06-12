---
title: "Openivo: a managed network of Mythbuntu boxes"
date: 2009-01-08
forum: Mythbuntu
---

### Post by openivo on 2009-01-08
A significant cost of consumer goods and services is marketing.
1.  The cost of gathering information about your customers
2.  The cost of getting information about your products and services to the customer.
The more accurate and reliable the information, the better return on investment for the seller, and the more value for the buyer.

The value of delivery of marketing information has been the primary method of financing television programming, through television commercials.  Cable and satellite providers have found that most viewers are also willing to pay additional costs for improved reception and a wider variety of programming.

The set-top box has been identified as an excellent source of marketing information.  Information for the seller (viewer demographics, interests, etc.) and information for the viewer, in the form of targeted or addressable advertising.  Several different systems are in various stages of implementation to use set-top box data to target tv commercials to particular geographic and demographic market segments.

If the set-top box is owned by the viewer, and if the box is such a valuable source and transmitter of marketing data, how can that value be captured by the viewer, instead of the satellite, cable, or TV network?

The Openivo system is a managed network of internet-connected personal computers with TV tuners running DVR software.  The DVR control data (shows watched, shows recorded, commercials watched, skipped, etc.) would be uploaded to the network via the internet connection.  No personally identifiable information (PII) would be collected.  The data would be analyzed and commercial video files would be downloaded to the set-top PC.  Extra commercials targeted to the needs and interests of the viewer would be added to the usual commercial breaks.  These commercials could also be skipped/FFWed, but many viewers will prefer to watch them, since they are tailored to their particular interests.

The marketing value to the advertisers should be in the range of $200 to $500 per year per subscriber.  This should be enough to completely finance the hardware, software, and monthly service with no fees to the subscriber.  In fact, a monthly rebate should be available to the subscriber 

A free computer-DVR and free DVR service in return for access to marketing data and some extra skip-able commercials.  Is it possible to give away that much value and run a large computing service on marketing and advertising?  Think Google.

Of course, Openivo could not just have a giveaway of millions of dollars of computers.  A plan with an initial fee for the cost of the hardware, with a rebate on installation and monthly rebate with use would be better.

By participating in this forum I hope:

1. To bounce my ideas off a bunch of smart people.

2. To find at least one skilled developer who shares the vision and is willing to devote time and energy to a cool project for some cash and possible equity in a new venture, all consistent with the GPL.

Marc

Marc Allan Feldman
Director and Owner
Openivo, Inc.

---

### Post by tgm4883 on 2009-01-08
Where to start.  

Good news:

Well the good news is that all of the watched behavior data is already kept in the db.  All you would have to do is write a small program to pull this information from the db and submit it.

Bad news:

You have a lot of work to do.  First, you may want to start (if you haven't already) getting contracts together with the broadcasting companies.  You will need their approval for this, as you will be messing with their stream.  Since you are dealing with advertising, you probably need to start hitting the local broadcasting affiliates, as you will need deals with them for the broadcasting.  Either you are going to sell the watched behavior to them, or you will pay them for advertising time.  You will also need someplace that the tailored commercials can be downloaded from.  

To me, you still have 2 basic problems.  First, you are trying to enter a market where other players already have a signifigant advantage over you.  Cable companies DVR's and TiVo already have the capabilities of gathering the data of what the consumer is watching.  They already sell this info to advertisers, and they don't want to mess with the stream.  They already have much more of this data than you do making it that much harder for you to succeed.  Second, it seems you want to insert yourself in the middle of something that already exists.  If someone is watching seinfeld on a local station, and there is a commedian performing locally that people might like, why would the commedian (or the place he is performing at) come to you to advertise when they could just buy a 30 second spot during the time that seinfeld is on?  It would definitly be cheaper for the advertiser to go directly to the station to advertise.

I don't mean to rain on your parade, I don't think this has a very good chance of happening.  Your problems aren't in the software, it's everything else that will be an issue.

PS.  You have a DVR company named Openivo.  I wouldn't think thats a hard sell for any judge on trademark infringement.

---

### Post by openivo on 2009-01-08
tgm4883,

Thanks for your response.

One reason to participate here is to identify challenges and I am very appreciative of your time and interest.

It is good to hear that you think the software issues are feasible.

As far as the legal and trademark issues go, the system is patent pending, the name "openivo" and the term "Personal TV" have been applied for trademark with the USPTO.  The intellectual property issues have been reviewed by our attorneys at RENNER, OTTO, BOISSELLE & SKLAR, LLP.

To collect and analyze the data, and to serve the tv commercial files, Openivo will use the Amazon Web Services infrastructure for cloud computing.  It is a very good fit for the application.

To clarify, although the Openivo system is patent pending and there will be proprietary software on the server side, all the software on the client computer will be maintained as FOSS. It will be an Open Source Computer Media Center. 

I hope this will be a major competitive advantage, as it will open the set-top computers for all kinds of potential modifications, plug-ins, etc. by the open source community.

Local stations have very limited inventory of commercial slots.  Most are controlled by the networks.  It should be far less expensive for businesses to identify the particular geographic and demographic market they want to reach and send the ads only to them.

Because the cable, satellite, and TiVo are public companies, they must be driven by profit.  Openivo is primarily driven by the motivation to keep television programming free and under the control of the viewer.

I think this system could be very cool.  Another aspect that will support the system is e-commerce.  The main menu will include a shopping option.  DVR control data would be used to identify products likely to be of interest to the viewer.  Item purchase with the remote should be doable.

At this point, Openivo has the intellectual property and a plan for the server system.  The next step is to develop and implement a prototype system.

We plan to start with a managed network with a small number of units in alpha testing.

I am looking for a developer with the skills and interest to move the system forward.  The client computer needs to:
1.  Work as a robust DVR
2.  Log and save all DVR control information in a file
3.  Automatically upload the file into Amazon Web Services
4.  Download commercial video files from AWS
5.  Integrates a web browser for e-commerce

Imagine the potential implication of a large networked open source computer media center system.  It could be a killer application to bring FOSS to the mass market.

I am hoping to find a developer willing to commit time and energy to the project because he or she thinks it is cool and shares our vision and mission.  I am willing to assign some cash as well to support their time.

Marc

---

