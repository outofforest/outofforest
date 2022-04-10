# DNA

This is how I work, it's hardcoded in my DNA.

> High-quality software is a result of great *software development process*.
> To produce great software focus on *the process* first.
> 
> *me*

## Software development strategies

There are three strategies of developing software I've learnt so far:
- marketing-driven development
- accounting-driven development
- engineering-driven development

### Marketing-driven development

It's a software development process where deadlines are set according to the dreams of the marketing department and founders.
Common sentences used in this environment:
- *We can't lose market momentum*
- *We will improve quality after we stop releasing new features*
- *This is extreme situation, we have to release this feature today*
- *We have to release today, deadline has been missed already*
- *We will add tests later*
- meetings, meetings... meetings everywhere

I don't work for marketing-driven software development companies. Reasons:
- Feature without tests can't be considered ready, it can't be released - no matter what
- If the team misses deadlines consistently, it means estimates are guessed improperly
- In such companies managers tend to organise more meetings to think they have more control, wasting everyone's time and making operations slower

### Accounting-driven development

It's a software development process where operations are optimised by bookkeepers.
Common sentences used in this environment:
- *You didn't turn off time counter for lunch*
- *Why did it take so long? You committed only 2 lines of code*
- *Code reviews waste time and money*

I don't work for accounting-driven software development companies. Reasons:
- Software development is 80% about thinking and 20% bout timing. If I take a lunch break I don't turn off thinking
- Quality assurance is not a cost, it's an investment
- *Characters typed per second* is the worst metric which could be used to evaluate software developer's efficiency

### Engineering-driven software development

This is the strategy where software developers are the owners of *software development process*.
Signs company uses this strategy:
- Code is properly managed (e.g.: linear history of repository, structure of code)
- Code is properly tested (unit tests, integration tests, CI, local infrastructure created on demand)
- Code is reviewed (code never reaches `main` branch until consensus is achieved)
- Processes are automated (linting, testing, releasing, reverting)
- Software developers are evaluated by examining quality of code, there are no deadlines (`dead` part is an awful misconception) but
  having a plan is still a good thing

This is the only type of company I work for.

## Software development environment

This is my opinion on how the software development process should look like. This is sad, and I don't know why the world looks like this
but more than 90% of software development companies who approach me miss all the points. I work only for those few where people are already aware of things
mentioned here or are ready to implement them. Of course, we learn from each other all the time, so I'm always open to new ideas. Entire live is an experiment.

### On-demand playground

The first thing I want to find in the code repository is the tool which, by executing one line in CLI, mimics the production environment
locally on my laptop. If software is made of 20 microservices I want to see them running on my computer without thinking about 20 magical commands being
composed manually. If those services need to talk to each other, they should be preconfigured correctly. If they need some external services
they should be able to reach them without my manual intervention.

Real world example: If you build next great omni-chain DeX using Tendermint and Cosmos SDK these are the components which should be preconfigured:
- validators for our  blockchain
- local devnets for all the other integrated blockchains (e.g.: Ethereum, other Tendermint-based blockchains)
- IBC relayers connecting all the chains
- Block explorers for every blockchain for manual inspection
- Access to the logs produced by all the services

This is a prerequisite for everything else. If company doesn't own one and does not agree to spend time on creating such tool I'm not going to cooperate.

### Development

The *on-demand playground* described above is then used by every developer to build new features. It's very convenient to be able to
play with new code manually during development, that's why having a local environment is so important.

Developers should be assessed by the quality of code they deliver, not time per character. It happens there are weeks when I spend
2-3 days on reading before even touching the code. There are moments when I find that to implement something correctly I must fix
a complex issue which hasn't been even considered during planning.

Real world example: Once I found that to configure virtual machine, FAT volume with configuration has to be created manually. Because there is no good go library for that
I decided to build one byte by byte, containing required files. To do it I had to read the FAT documentation and experiment with `vfat` driver on Linux. It took
much more time than everyone expected.

I don't work for companies trying to punish me in any way in such situation.

### Integration tests

The *on-demand playground* is also used to run integration tests. It should be possible to run those tests locally by each developer individually
to ensure that after making a change nothing is broken. The test framework should connect to a *playground* and use it like a production
environment, making API calls, querying state etc.

The same setup playground+tests setup should be used in CI to prevent any changes violating the tests from being merged into `main` branch.

Real world example: Having our great DeX we want to implement integration tests checking that token transfers between all the blockchains
work correctly, supply is preserved and relayers move funds between blockchains correctly.

Real world example 2: Cosmos SDK is not-so-perfect piece of software, and it happens that serious bugs are introduced between releases.
That's why all the features have to be covered.

This is also my hard requirement. Blockchains hold billions of $$$. I don't work for companies where people don't care. They will lose funds one day.

### Monitoring

Production environment should be constantly monitored. I'm not talking only about DevOp stuff like resources, servers, network etc.
I mean constant monitoring of business logic operations.

Real world example: check if nodes are constantly able to sync with mainnet. 

### Reviews

This is the most important part of software development process. Even experienced developer makes stupid mistakes. He/She may be just tired and miss something important.
Despite that, doing review is the best way of learning and improving the skill-set. People may know libraries I don't, people may even know some language construct I don't.
Being reviewed and reviewing are the more skill-developing strategies I've ever found.

I don't work for companies who find code reviews to be waste of time and money.

## Special notes on DeFi

I'm approached by tons of companies entering hot DeFi market. The great majority of them don't care about stuff I described above.
Looks like their founders (often described as "serial entrepreneurs") just dream about fast money. In any case their blockchain fails and funds are lost
they will just go to another VC fund and get money for next "innovative start-up". I don't work for such companies.

For me, DeFi software is like a banking system. It may crash from time to time (panics happen in every software) but it can't lose funds.
That's why it has to be developed, tested and maintain like a banking system.

## Holidays

I don't understand why, but I find it to be a problem in some organizations. We develop software doing critical stuff, right? We are not robots, right?
That's why we need breaks, holidays, day offs etc. from time to time.

You may expect me:
- to take about 6 weeks of holidays during the year, usually 3 * 2 weeks
- to take day offs matching catholic holidays in Poland (~12 days per year)
- to take some sparse day offs when I must do some errands (just a few days per year)
- to take day offs when I'm sick (once or twice per year)

There were companies who paid me just for time I really spent working and those who paid me a flat monthly rate allowing me
to take UPTOs whenever I liked. I accept both policies.
