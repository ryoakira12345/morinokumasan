進める上での注意点  
①目的の解釈はきちんと出来ていたか  
②目的に沿った、分析方法を設定できていたか  
③分析方法に使えるデータが準備できているか  
④次のアクションに繋がる結果になっているか  
※「分析」＝「可視化」では無い点に注意。「可視化」だけでは相手に伝わらない。  

# １．課題の見極め（目的の明確化）
## （１）目的の明確化
データ分析を行う目的と、必要とされる結果を明確にする。  
データ分析は現状把握だけでは不十分で、問題解決に必要な打ち手まで提案できることが求められる。  
また、どんなに精度の高い結果を得たとしても、目的に一致していなければ意味がない。

## （２）仮説を立てる
ここで立てる仮説とは、「分析して知りたいこと」に対する仮の答えとなる。  
例えば、「原因は○○だ」、「○○の対策を行えば、△△になるはずだ」などとなる。  
「◇◇が減った」では不十分。  
闇雲にデータ分析を行うのではなく、ある程度の仮説を持って分析した方が結果に早くたどり着くケースが多い。  
仮説は必ずしも正解である必要は無く、データ分析を進めて行くことで、仮説を修正していけば良い。  

# ２．現状分析
## （１）分析方法を決める
立てた仮説に対して、適切な分析手法を決める。RFM分析、時系列分析などもその一つ。  
「データ分析」は「現状分析」であり、「現状分析」は目標を決めるために必要な作業である。  
取得データから各種の統計量を取得したり、グラフで可視化したりといった作業は現状を知る作業であり、それによって得られた情報は予測対象の明確化に必要となる。  

## （２）分析に使用する情報（データ）を決める
回帰、分類などの分析方法によって必要なデータは変わる。  
慣れないうちは今あるデータから結果を取得できる方法を検討するケースが多いが、目標を決めておかないといつまでもやり続けることが多いので注意。  
（データの海に溺れる）

## （３）情報（データ）を確認する
集めたデータが分析に使用できるかを確認する。  
データの中に分析に必要な情報が含まれていなければ、欲しい結果を得ることはできない。  
「取得したデータの分析をせずにとりあえず機械学習の手法を試してみる」というのは避けた方が良い。  
不必要なデータを学習させても、不必要な結果しか反映されない。（garbage in garbage out）  
### データの確認方法
・平均や分散、相関係数といったデータの特徴を示す基礎的な統計量を確認する。  
・グラフによる可視化を行い、統計量ではわからないデータの具体的な分布や性質を把握する。  
・その他、データの特徴の把握  
・季節変動がないか？天候や自然災害などから異常なデータが取得された時期がないか？  
### 必要な知識
効率よく分析するためには、データの意味を理解する必要がある。  
具体的にいえば特定のテーブルの特定のカラムは何を意味するのか？ 予測対象の情報はどのテーブルを見ればよいのか？ といった問いに答えられる必要がある。  
その為には、データの取得元となる「情報システムや業務システムに対する理解」が必要となる。  

## （４）分析
これまでのステップで決めた内容に沿って分析を行う。  
また、分析中に得られた知見から一歩踏み込んだ分析も行う。  
例えば、売上を予想したい場合、以下のような確認が必要となる。  
１．売上と相関の高い情報は何か？  
２．その情報は、実際の予測環境化でも取得できる情報か？  
３．季節変動が与える影響はどの程度か？  
1.については、その情報と売上の相関係数から機械学習を行った場合の精度に見当をつけられる。  
どの程度の精度を出すことが目標になるか？ といったことも検討できる。  
2.については、検証用に取得したデータに実際の予測環境では得られない情報が含まれている場合があるので注意が必要である。  
これはデータ分析におけるLeakageと呼ばれる問題であり、モデルを作るときに、本来知らないはずの情報（変数やデータ）を不当に使ってしまうことである。  
3.の季節変動は扱いを考慮すべき問題である。  
例えば、年度末やセールの時期は普段と異なる売上となる。  
このような異常とも取れる売上の増減の扱いは十分に検討する必要がある。  

# ３．施策の立案
## （１）特徴量の選択
モデルに学習させる特徴量（パラメータ）を選択する。  

## （２）モデルの選択とデータの前処理
予測対象に対する適切な最適化アルゴリズムを選択する。  
「予測対象に対する適切な最適化アルゴリズムの選定」については、どんな問題に対しても万能な手法は存在しないため、最良の方法を選定する必要がある。  
例えば、CNN（畳み込みニューラルネットワーク）は画像判別に強く、RNN（リカレントニューラルネットワーク）は時系列データに強いが、ほかのどんな状況においても万能なわけではない。  

## （３）データの前処理
「質の良いデータを集めること」が良いモデルを作るために必要となる。  
予測をするために必要な学習データは、正解と不正解のデータが同じ量が必要となる。  
通常、同じ量のデータを集めることは困難なため、ダミーデータを用意することになるが、ダミーデータの品質が予測結果の精度に影響する点に注意が必要である  

## （４）モデルの作成、評価
モデルを作成し、精度を評価する。  
「予測対象や機械アルゴリズムに見合った計算資源」については、その予想をするには、機械学習アルゴリズムに対する理解が助けとなる。  
例えば、ディープラーニングは大量のデータと計算資源が必要である。  
長時間かけて学習させても良い結果が得られず、モデルやデータに工夫を施し再度学習を行うケースがよくある。  

## （５）モデルの評価
モデルの評価・・・ 
