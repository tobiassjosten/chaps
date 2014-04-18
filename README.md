# Chaps — Manage your lads, chums and fellas

*Chaps* is a command line tool to help you manage the lists of people you follow on various online services.

If you've ever wondered who doesn't follow you back on Twitter, wanted to see whom your friends are following on GitHub but you are not or if you wish to follow back all your fans on Instagram — Chaps is for you!

See [What do you think of Chaps?](http://vvv.tobiassjosten.net/projects/what-do-you-think-of-chaps) for more details.

## Supported services

Chaps support Facebook, GitHub, Google+, Instagram and Twitter. Are you missing your favorite service? Just [create an issue](https://github.com/tobiassjosten/chaps/issues/new) and explain the why and how of adding it.

Prefix symbols are used to differentiate between the various online services. For example the account +TobiasSjosten means *TobiasSjosten on Google+*, @tobiassjosten means *tobiassjosten on Twitter*, and so on.

The following is a legend for the supported services and their prefix symbols.

Facebook: $tobiassjosten  
GitHub: &tobiassjosten  
Google: +TobiasSjosten  
Instagram: #tobiassjosten  
Twitter: @tobiassjosten  

## List your chaps

Chaps have a couple of commands to let you interact with your online services. The most basic command is `list`, which simply prints a list of the people you follow and/or are following a given account.

    $ chaps list @tobiassjosten
    @somedude following:yes leading:no
    @somedudette following:no leading:yes
    @anotherdude following:no leading:no
    @anotherdudette following:yes leading:yes

## Filter your chaps

By default `list` will show you all your chaps; both people you are following and the ones who are following you. In some cases you only want a segment of them and this is when you use filters.

Your *following* are the people who follow you, regardless of whether you follow them back or not. You can toggle this group using either `+following` to include only people following you or `-following` to exclude them.

    $ chaps list +following @tobiassjosten
    @somedude following:yes leading:no
    @anotherdudette following:yes leading:yes

    $ chaps list -following @tobiassjosten
    @somedudette following:no leading:yes
    @anotherdude following:no leading:no

Your *leading* are the people you are following, no matter if they follow you or not. You toggle this group using either `+leading` to include only people you follow or `-leading` to exclude them.

    $ chaps list +leading @tobiassjosten
    @somedudette following:no leading:yes
    @anotherdudette following:yes leading:yes

    $ chaps list -leading @tobiassjosten
    @somedude following:yes leading:no
    @anotherdude following:no leading:no

In summary; Chaps will by default list all people whom a given account is related to and filters work off of this list.

## Authorization

In order to do something useful with Chaps we must first authorize an account. This is done with the `authorize` command:

    $ chaps authorize

Follow the instructions and you will soon have your new account added. Using the `accounts` command you can easily see all authorized accounts.

    $ chaps accounts
    Twitter: @tobiassjosten @smartburk
    Google+: +TobiasSjosten

Remember: you don't need to authorize an account to use it with Chaps. Even if you don't own the Twitter account *justinbieber* you can still list all beliebers.

    $ chaps list +following @justinbieber
    @somedude following:yes leading:no
    @somedudette following:yes leading:no
    @anotherdude following:yes leading:no
    @anotherdudette following:yes leading:no

Authorization is only required to take action on a given list of chaps.

## Actions

There are two action commands; `follow` and `unfollow`.

To decide which accounts to follow and unfollow you feed Chaps a comma separated `list` parameter:

    $ chaps follow --list=@somedude,@anotherdudette @tobiassjosten
    @tobiassjosten followed @somedude and @anotherdudette

You can also use STDIN to feed Chaps accounts. There is not required format but all recognized accounts (using the known prefix symbols) will be used.

    $ echo @somedude @anotherdudette | chaps follow @tobiassjosten
    @tobiassjosten followed @somedude and @anotherdudette

Because the output of the `list` command gives us a nice heap of accounts, we can re-use that to take action on them.

    $ chaps list +following @tobiassjosten | chaps follow @tobiassjosten
    @tobiassjosten followed @somedude @anotherdude

As you can see we are using two accounts here. One for the listing and another for taking the action. This means we could just as well use two separate accounts. Let's get rid of all the beliebers:

    $ chaps list +following @justinbieber | chaps unfollow @tobiassjosten
    @tobiassjosten unfollowed @somedude, @somedudette, @anotherdude and @anotherdudette

## But … where is it?!

Sorry to disappoint but Chaps is currently no more than this README. I decided to approach this project using [readme driven development](http://tom.preston-werner.com/2010/08/23/readme-driven-development.html) and this is the first deliverable.

If you have any feedback at all (even if it's just "this sucks" or "yes please") — I'd love to hear from you! Just [create an issue](https://github.com/tobiassjosten/chaps/issues/new) with your thoughts and let's have a chat.

See [What do you think of Chaps?](http://vvv.tobiassjosten.net/projects/what-do-you-think-of-chaps) for more details.
