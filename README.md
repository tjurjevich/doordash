# Doordash Delivery Time Estimate

This project attempts to estimate the time from order to delivery for various doordash markets. Four model types are trained and tested for this project: random forest regressor, XGBoost regressor, generalized additive model (GAM), and neural network. These models use the following 8 predictor variables for input: market_id, order_protocol, hr_created, busy_dasher_pct, estimated_store_to_consumer_driving_duration, total_outstanding_orders, subtotal, and num_distinct items. These 8 predictor variables aim to accurately predict the customer wait time in seconds. Three metrics are calculated to interpret model efficiency: mean absolute error (MAE), mean squared error (MSE), and mean absolute percentage error (MAPE). 

Only one model, the deep learning model, breaks the 700-second MAE mark. This NN includes 2 hidden layers--each containing 128 units. To encourage fine-tuning, `callback1` is added, which adds a learning rate adjustment to the model starting at epoch 25. To discourage overfitting, `callback2` is added, which stops NN training if there is not a 0.0001 decrease in `val_loss` over the span of 25 epochs.

The GAM proved to be the second best model, while the random forest and XGBoost regressor models performed relatively subpar. Other models could certainly be explored for this dataset--which include various types of linear regression (OLS, ridge, lasso), bayesian regression, or queuing model.

