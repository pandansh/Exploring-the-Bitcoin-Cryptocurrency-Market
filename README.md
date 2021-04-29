# Exploring-the-Bitcoin-Cryptocurrency-Market
Exploring the Bitcoin Cryptocurrency Market with Python(Numpy, Pandas, Seaborn) on Coinmarket_Cap(2017-2018) Datasets

1. Bitcoin and Cryptocurrencies: Full dataset, filtering, and reproducibility
Since the launch of Bitcoin in 2008, hundreds of similar projects based on the blockchain technology have emerged. We call these cryptocurrencies (also coins or cryptos in the Internet slang). Some are extremely valuable nowadays, and others may have the potential to become extremely valuable in the future1. In fact, on the 6th of December of 2017, Bitcoin has a market capitalization above $200 billion.

![image](https://user-images.githubusercontent.com/62187736/116493620-3387f700-a8f3-11eb-966b-f3c11a96e59c.png)
The astonishing increase of Bitcoin market capitalization in 2017.
*1 WARNING: The cryptocurrency market is exceptionally volatile2 and any money you put in might disappear into thin air. Cryptocurrencies mentioned here might be scams similar to Ponzi Schemes or have many other issues (overvaluation, technical, etc.). Please do not mistake this for investment advice. *

2 Update on March 2020: Well, it turned out to be volatile indeed :D

That said, let's get to business. We will start with a CSV we conveniently downloaded on the 6th of December of 2017 using the coinmarketcap API (NOTE: The public API went private in 2020 and is no longer available) named datasets/coinmarketcap_06122017.csv.

2. Discard the cryptocurrencies without a market capitalization
Why do the count() for id and market_cap_usd differ above? It is because some cryptocurrencies listed in coinmarketcap.com have no known market capitalization, this is represented by NaN in the data, and NaNs are not counted by count(). These cryptocurrencies are of little interest to us in this analysis, so they are safe to remove.

3. How big is Bitcoin compared with the rest of the cryptocurrencies?
At the time of writing, Bitcoin is under serious competition from other projects, but it is still dominant in market capitalization. Let's plot the market capitalization for the top 10 coins as a barplot to better visualize this.

![image](https://user-images.githubusercontent.com/62187736/116493877-c032b500-a8f3-11eb-9565-35b8dcb75e70.png)

4. Making the plot easier to read and more informative
While the plot above is informative enough, it can be improved. Bitcoin is too big, and the other coins are hard to distinguish because of this. Instead of the percentage, let's use a log10 scale of the "raw" capitalization. Plus, let's use color to group similar coins and make the plot more informative1.

For the colors rationale: bitcoin-cash and bitcoin-gold are forks of the bitcoin blockchain2. Ethereum and Cardano both offer Turing Complete smart contracts. Iota and Ripple are not minable. Dash, Litecoin, and Monero get their own color.

1 This coloring is a simplification. There are more differences and similarities that are not being represented here.

2 The bitcoin forks are actually very different, but it is out of scope to talk about them here. Please see the warning above and do your own research.

![image](https://user-images.githubusercontent.com/62187736/116494263-9201a500-a8f4-11eb-87ca-186c63357e87.png)

5. What is going on?! Volatility in cryptocurrencies
The cryptocurrencies market has been spectacularly volatile since the first exchange opened. This notebook didn't start with a big, bold warning for nothing. Let's explore this volatility a bit more! We will begin by selecting and plotting the 24 hours and 7 days percentage change, which we already have available.

               percent_change_24h  percent_change_7d
id                                                  
flappycoin                 -95.85             -96.61
credence-coin              -94.22             -95.31
coupecoin                  -93.93             -61.24
tyrocoin                   -79.02             -87.43
petrodollar                -76.55             542.96

6. Well, we can already see that things are a bit crazy
It seems you can lose a lot of money quickly on cryptocurrencies. Let's plot the top 10 biggest gainers and top 10 losers in market capitalization.

![image](https://user-images.githubusercontent.com/62187736/116494351-c07f8000-a8f4-11eb-8b62-6f7230e56723.png)

7. Ok, those are... interesting. Let's check the weekly Series too.
800% daily increase?! Why are we doing this tutorial and not buying random coins?1

After calming down, let's reuse the function defined above to see what is going weekly instead of daily.

1 Please take a moment to understand the implications of the red plots on how much value some cryptocurrencies lose in such short periods of time

![image](https://user-images.githubusercontent.com/62187736/116494414-e016a880-a8f4-11eb-89f9-3e3f554f2a1e.png)

8. How small is small?
The names of the cryptocurrencies above are quite unknown, and there is a considerable fluctuation between the 1 and 7 days percentage changes. As with stocks, and many other financial products, the smaller the capitalization, the bigger the risk and reward. Smaller cryptocurrencies are less stable projects in general, and therefore even riskier investments than the bigger ones1. Let's classify our dataset based on Investopedia's capitalization definitions for company stocks.

1 Cryptocurrencies are a new asset class, so they are not directly comparable to stocks. Furthermore, there are no limits set in stone for what a "small" or "large" stock is. Finally, some investors argue that bitcoin is similar to gold, this would make them more comparable to a commodity instead.

             id  market_cap_usd
0       bitcoin    2.130493e+11
1      ethereum    4.352945e+10
2  bitcoin-cash    2.529585e+10
3          iota    1.475225e+10

9. Most coins are tiny
Note that many coins are not comparable to large companies in market cap, so let's divert from the original Investopedia definition by merging categories.

This is all for now. 

![image](https://user-images.githubusercontent.com/62187736/116494475-00466780-a8f5-11eb-8641-a91472d1c1fc.png)
