# VK Test assignment
Для решения задачи решил выбрать два градиентных бустинга (XGBoostRanker, LightGBMRanker), поскольку они лучше всего нынче справляются с табличными данными. Гиперпараметры перебирал с помощью либы optuna. Предварительно проверил тест Граббса (/notebooks/data-check.ipynb) и выявил, что почти в каждом (!) столбце есть выбросы. Но всё равно сначала решил попробовать тюнить на изначальных данных, после чего уже стандартизировал с помощью StandartScaler`a из sklearn.preprocessing.

Получил следующие результаты:

1) Best NDCG@5 for LGBM: 0.5374
Best hyperparameters for LGBM:
{'num_leaves': 87, 'max_depth': 9, 'learning_rate': 0.10264292610732471, 'num_boost_round': 336, 'min_child_samples': 35, 'reg_alpha': 0.14067762968187958, 'reg_lambda': 0.7409153013004788}

2) Best NDCG@5 for XGB: 0.5436
Best hyperparameters for XGB:
{'learning_rate': 0.18355585767238483, 'max_depth': 9, 'n_estimators': 456, 'min_child_weight': 2, 'gamma': 0.007183842663282607, 'subsample': 0.9619329921087644, 'colsample_bytree': 0.5487403237135628, 'reg_alpha': 0.46590326161117473, 'reg_lambda': 0.05390754790505921}

3) Best NDCG@5 for LGBM on normalized data: 0.5517
Best hyperparameters for LGBM on normalized data:
{'num_leaves': 49, 'max_depth': 10, 'learning_rate': 0.10523945951163613, 'num_boost_round': 245, 'min_child_samples': 46, 'reg_alpha': 0.14230649990869138, 'reg_lambda': 0.13435149240608613}

4) Best NDCG@5 for XGB on normalized data: 0.5416
Best hyperparameters for XGB on normalized data:
{'learning_rate': 0.13541471418335874, 'max_depth': 10, 'n_estimators': 475, 'min_child_weight': 8, 'gamma': 0.055597247241479325, 'subsample': 0.7993063842562708, 'colsample_bytree': 0.8843911166501889, 'reg_alpha': 0.6321697450018331, 'reg_lambda': 0.4244566664938659}
